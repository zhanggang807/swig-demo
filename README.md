### Steps :

* download swig-3.0.3 from http://www.swig.org/download.html

* tar -zxvf swig-3.0.3.tar.gz, cd swig-3.0.3

* configure, make, sudo make install

* create a temp dir named swig-demo then cd swig-demo 

* create example.c example.i, source code in http://www.swig.org/tutorial.html

* swig -java example.i

* gcc -fPIC -I$JAVA_HOME/include -I$JAVA_HOME/include/linux -c example.c example_wrap.c

* gcc -shared example.o example_wrap.o -o libexample.so 

* create Main.java file, content is :
```java
public class main {
    public static void main(String args[]) {
        System.loadLibrary("example");
        System.out.println(example.getMy_variable());
        System.out.println(example.fact(5));
        System.out.println(example.get_time());
    }
}
```
* javac Main.java

* create run.sh , content is :
```shell
#!/bin/bash
export LD_LIBRARY_PATH
java Main
```
* chmod u+x run.sh, then ./run.sh

### Offical Documentation about SWIG and java

* http://www.swig.org/Doc1.3/Java.html
