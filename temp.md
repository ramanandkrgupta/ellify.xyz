**UNIT 4: Polymorphism**  
**Core Concept**: Polymorphism (Greek: "many forms") enables objects to take different forms, allowing one interface to represent multiple behaviors. It enhances flexibility and code reusability in object-oriented programming (OOP).

---

### **1. Method Overloading**  
- **Definition**: Multiple methods in the **same class** share the same name but have **different parameters** (type, number, or order).  
- **Key Points**:  
  - **Compile-time (Static) Polymorphism**: The method to execute is determined during compilation.  
  - **Rules**:  
    - Must differ in parameter lists (return type alone is insufficient).  
    - Can have different access modifiers or return types.  
  - **Example**:  
    ```java
    class Calculator {
      int add(int a, int b) { return a + b; }
      double add(double a, double b) { return a + b; } // Overloading
    }
    ```

---

### **2. Method Overriding**  
- **Definition**: A subclass provides a **specific implementation** for a method already defined in its superclass.  
- **Key Points**:  
  - **Runtime (Dynamic) Polymorphism**: The JVM decides which method to invoke based on the **object's type** at runtime.  
  - **Rules**:  
    - Method name, parameters, and return type (covariant allowed) must match the superclass.  
    - Access modifier in subclass must be **as or more visible** than the superclass method.  
    - Cannot override `final`, `static`, or `private` methods.  
  - **Example**:  
    ```java
    class Animal {
      void sound() { System.out.println("Animal sound"); }
    }
    class Dog extends Animal {
      @Override
      void sound() { System.out.println("Bark"); } // Overriding
    }
    ```

---

### **3. Static vs. Runtime Polymorphism**  
| **Feature**              | **Static (Compile-Time)**         | **Runtime (Dynamic)**             |  
|--------------------------|-----------------------------------|-----------------------------------|  
| **Mechanism**            | Method Overloading                | Method Overriding                 |  
| **Resolution**           | Based on reference type           | Based on object type              |  
| **Binding**              | Early binding (compile time)      | Late binding (runtime)            |  
| **Example**              | `add(int, int)` vs. `add(double, double)` | `Animal a = new Dog(); a.sound()` |  

---

### **4. Key Differences**  
- **Overloading**:  
  - Same class, different parameters.  
  - Enhances readability by reusing method names.  
- **Overriding**:  
  - Subclass redefines superclass method.  
  - Enables runtime flexibility (e.g., interface implementations).  

---

### **5. Benefits of Polymorphism**  
1. **Code Reusability**: Write generic code for superclasses that works with all subclasses.  
2. **Flexibility**: Easily extend systems by adding new subclasses.  
3. **Maintainability**: Reduce code complexity by centralizing logic.  

---

**Example of Runtime Polymorphism**:  
```java
class Shape {
  void area() { System.out.println("Calculate area"); }
}
class Circle extends Shape {
  @Override
  void area() { System.out.println("πr²"); }
}
class Test {
  public static void main(String[] args) {
    Shape s = new Circle(); // Upcasting
    s.area(); // Output: πr² (Runtime decision)
  }
}
```

---

**Summary**:  
- **Method Overloading**: Same name, different parameters; resolved at compile time.  
- **Method Overriding**: Subclass redefines superclass method; resolved at runtime.  
- Polymorphism simplifies code design and promotes scalable, maintainable systems.