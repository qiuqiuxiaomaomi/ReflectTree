# ReflectTree
Java的反射技术研究

<pre>
反射机制

      反射机制是Java语言提供的一种基础功能，赋予程序在运行时自省的能力，通过反射我们可以直接操作
      类或者对象，比如获取某个对象的类定义，获取类声明的属性，方法，调用方法或者构造对象，甚至可以
      运行时修改类定义。

      反射最大的作用之一就在于我们可以不在编译时知道某个对象的类型，而在运行时通过提供完整的
      ”包名+类名.class”得到。注意：不是在编译时，而是在运行时

      功能：
          •在运行时能判断任意一个对象所属的类。
          •在运行时能构造任意一个类的对象。
          •在运行时判断任意一个类所具有的成员变量和方法。
          •在运行时调用任意一个对象的方法。
          
      说大白话就是，利用Java反射机制我们可以加载一个运行时才得知名称的class，获悉其构造方法，并
      生成其对象实体，能对其fields设值并唤起其methods。

      应用场景：
         反射技术常用在各类通用框架开发中。因为为了保证框架的通用性，需要根据配置文件加载不同的对
         象或类，并调用不同的方法，这个时候就会用到反射——运行时动态加载需要加载的对象。

      特点：
         由于反射会额外消耗一定的系统资源，因此如果不需要动态地创建一个对象，那么就不需要用反射。
         另外，反射调用方法时可以忽略权限检查，因此可能会破坏封装性而导致安全问题。
</pre>

<pre>
动态代理
      动态代理是一种方便运行时动态构建代理，动态处理代理方法的机制，很多场景都是利用类似机制做到的
      ，比如用来包装RPC调用，面向切面编程AOP等。

      为其他对象提供一种代理以控制对这个对象的访问。在某些情况下，一个对象不适合或者不能直接引用另
      一个对象，而代理对象可以在两者之间起到中介的作用（可类比房屋中介，房东委托中介销售房屋、签订
      合同等）。

      所谓动态代理，就是实现阶段不用关心代理谁，而是在运行阶段才指定代理哪个一个对象（不确定性）。
      如果是自己写代理类的方式就是静态代理（确定性）。

      组成要素：
         (动态)代理模式主要涉及三个要素：
              其一：抽象类接口
              其二：被代理类（具体实现抽象接口的类）
              其三：动态代理类：实际调用被代理类的方法和属性的类

      实现方式:
          实现动态代理的方式很多，比如 JDK 自身提供的动态代理，就是主要利用了反射机制。还有其他
          的实现方式，比如利用字节码操作机制，类似 ASM、CGLIB（基于 ASM）、Javassist 等。

          举例，常可采用的JDK提供的动态代理接口InvocationHandler来实现动态代理类。其中invoke
          方法是该接口定义必须实现的，它完成对真实方法的调用。通过InvocationHandler接口，所有
          方法都由该Handler来进行处理，即所有被代理的方法都由InvocationHandler接管实际的处理
          任务。此外，我们常可以在invoke方法实现中增加自定义的逻辑实现，实现对被代理类的业务逻
          辑无侵入。
</pre>
