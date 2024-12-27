# Utility Types

## Awaited<Type>

Obtém o tipo de uma Promise, pode obter o tipo recursivamente.

```typescript
type A = Awaited<Promise<string>>; 
// type A = string
type B = Awaited<Promise<Promise<number>>>;
// type B = number
type C = Awaited<boolean | Promise<number>>;
// type C = boolean | number;
```

Mais util quando usando juntamente com `ReturnType`.

```typescript
function getName(): Promise<string> {
  return Promise.resolve("Carlos");
}

type Name = Awaited<ReturnType<typeof getName>>;
```

## Partial<Type>

Constrói um tipo com todas as propriedades de `Type` definidas como opcional.

```typescript
interface Person {
  name: string;
  email: string;
}

function updatePerson(person: Person, fieldsToUpdate: Partial<Person>) {
  return {...person, ...fieldsToUpdate};
}

const person: Person = {
  name: "João",
  email: "joao@gmail.com"
};

updatePerson(person, { name: "João Carlos"});
```