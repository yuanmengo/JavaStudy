仔细看这个继承代码例子的三个**实例化dog1, dog2, dog3**。看看**输出的区别**!!!
```java
public class Animal {
    public int id;
    public String name;
    public int age;
    public int weight;

    public Animal(int id, String name, int age, int weight) {
        this.id = id;
        this.name = name;
        this.age = age;
        this.weight = weight;
    }

    public void sayHello() {
        System.out.println("Hello");
    }

    public void eat() {
        System.out.println("Eat");
    }

    public void sing() {
        System.out.println("Sing");
    }
}

class Dog extends Animal {
    public Dog(int id, String name, int age, int weight) {
        super(id, name, age, weight);// 调用父类的构造方法
    }

    public void WanWan() {
        System.out.println("WanWan");
    }

    @Override
    public void sayHello() {
        System.out.println("Hello, I am a Dog");
    }
}

class AnimalTest {
    public static void main(String[] args) {
        System.out.println("-----dog1-----");
        Animal dog1 = new Dog(1, "Dog", 2, 30);
        dog1.sayHello(); //Hello, I am a Dog
        dog1.eat();
        dog1.sing();
        // dog2.WanWan();因为WanWan()方法是Animal的子类Dog里的，所以不能调用子类的WanWan()方法

        System.out.println("-----dog2-----");
        Animal dog2 = new Animal(1, "Dog", 2, 30);
        dog2.sayHello();//Hello
        dog2.eat();
        dog2.sing();
        // dog2.WanWan();因为WanWan()方法是Animal的子类Dog里的，所以不能调用子类的WanWan()方法

        System.out.println("-----dog3-----");
        Dog dog3 = new Dog(1, "Dog", 2, 30);//Hello, I am a Dog
        dog3.sayHello();
        dog3.eat();
        dog3.sing();
        dog3.WanWan();
    }
}
```
### 终端的输出结果:
![image](https://github.com/yuanmengo/JavaStudy/assets/93896276/9e216743-71e4-484c-bdae-a453a0a8e948)
