*This project has been created as part of the 42 curriculum by rmanzana*

# C++ Module 04 — Subtype polymorphism, abstract classes and interfaces

## Description

Fifth module of the 42 C++ piscine. It is about **runtime polymorphism**: calling the right function through a base class pointer with `virtual` functions, **deep copies** of objects that own dynamic memory, **abstract classes** that cannot be instantiated, and **interfaces** (classes with only pure virtual functions).

All the code follows the **C++98** standard and compiles with `c++ -Wall -Wextra -Werror -std=c++98`.

## Exercises

| Exercise | Program | Description |
|---|---|---|
| `ex00` — Polymorphism | `animal` | An `Animal` base class with a `virtual makeSound()`, and `Dog` and `Cat` derived classes. Through an `Animal*`, each makes its own sound. A `WrongAnimal` / `WrongCat` pair **without** `virtual` shows the difference: the base version is called instead. |
| `ex01` — I don't want to set the world on fire | `animal` | `Dog` and `Cat` now own a `Brain` (100 ideas) allocated with `new`. Copying an animal must create a **deep copy** of its brain, not share the pointer. An array of animals is created and deleted through `Animal*`, which requires a **virtual destructor** to avoid leaks. |
| `ex02` — Abstract class | `animal` | `Animal` becomes **abstract** (`AAnimal`, with a pure virtual function), so a generic animal can no longer be instantiated. |
| `ex03` — Interface & recap | `rol` | A small RPG-like system: `AMateria` (abstract), the concrete materias `Ice` and `Cure`, the interfaces `ICharacter` and `IMateriaSource`, and their implementations `Character` (an inventory of 4 materias) and `MateriaSource` (learns materia templates and creates new ones with `clone()`). Combines everything: abstract classes, interfaces, deep copies and memory ownership. |

## Key concepts

- **`virtual` functions and dynamic dispatch:** the function called depends on the real type of the object, not on the type of the pointer.
- **Virtual destructors:** required in any base class that is deleted through a base pointer.
- **Deep copy vs shallow copy** for classes that own dynamically allocated memory.
- **Pure virtual functions** (`= 0`) and **abstract classes**.
- **Interfaces:** classes with only pure virtual functions, used to define a contract.
- **The prototype pattern:** creating new objects with `clone()`.

## Instructions

Each exercise has its own `Makefile`:

```bash
cd ex03
make
./rol
```

`make clean`, `make fclean` and `make re` are available in every exercise. Memory leaks can be checked with `valgrind --leak-check=full`.

## Resources

- [cplusplus.com — Polymorphism](https://cplusplus.com/doc/tutorial/polymorphism/)
- [LearnCpp.com — Virtual functions and polymorphism](https://www.learncpp.com/cpp-tutorial/virtual-functions/)
- [LearnCpp.com — Virtual destructors](https://www.learncpp.com/cpp-tutorial/virtual-destructors-virtual-assignment-and-overriding-virtualization/)
- [Object copying — Shallow vs deep copy](https://en.wikipedia.org/wiki/Object_copying)
- [Prototype pattern — Refactoring.Guru](https://refactoring.guru/design-patterns/prototype)
