---
title: "Eclipse problem, cannot find JDK 7"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by WubiAR on 2011-08-04
Hello there, Just installed eclipse from the software centre and I am getting this message when I try to open it:    >  A Java Runtime Environment (JRE) or Java Development Kit (JDK) must be available in order to run Eclipse. No Java virtual machine was found after searching the following locations: /usr/lib/eclipse/jre/bin/java java in your current PATH   My JDK 7 is located: /usr/lib/jvm/jdk1.7.0  How do I change the location that it is searching for, so that it can identify my JDK?

---

### Post by lkjoel on 2011-08-04
Try this in a Terminal window:
```
sudo add-apt-repository ppa:lkjoel/javainstaller
sudo apt-get update
sudo apt-get install javainstaller
/usr/bin/javainstall.sh

```

---

### Post by WubiAR on 2011-08-04
> **lkjoel said:**
> Try this in a Terminal window:
```
sudo add-apt-repository ppa:lkjoel/javainstaller
sudo apt-get update
sudo apt-get install javainstaller
/usr/bin/javainstall.sh

```

  Unfortunately, I still get that error, even after I typed through all of those commands.

---

### Post by lkjoel on 2011-08-04
Could you give me the output of this Terminal command:
```
echo $PATH

```

---

### Post by WubiAR on 2011-08-04
> **lkjoel said:**
> Could you give me the output of this Terminal command:
```
echo $PATH

```

 Typing in that command into the terminal, I get this output:  

> /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games 

---

### Post by fdrake on 2011-08-04
in eclipse go to window > preferences > java (from the left menu bar)>classpath> change the path

---

### Post by WubiAR on 2011-08-04
> **fdrake said:**
> in eclipse go to window > preferences > java (from the left menu bar)>classpath> change the path

The problem is that I can't open the program itself. This error pops up, I press OK, and Eclipse does not open.

---

### Post by fdrake on 2011-08-04
from the manual
```
man eclipse
..........
       -vm <path to java vm> (Executable, Main)
              When passed to the Eclipse executable, this option is used to locate the Java VM to use to run Eclipse. It
              should be the full file system path to an appropriate:  Java  jre/bin  directory,  Java  Executable,  Java
              shared  library  (libjvm.so),  or  a Java VM Execution Environment description file. If not specified, the
              Eclipse executable uses a search algorithm to locate a suitable VM. In  any  event,  the  executable  then
              passes the path to the actual VM used to Java Main using the -vm argument. Java Main then stores this val&#8208;
              ue in eclipse.vm.
..............
```
you could use 
```
eclipse -vm <your jvm path>
```

---

### Post by WubiAR on 2011-08-05
> **fdrake said:**
> from the manual
```
man eclipse
..........
       -vm <path to java vm> (Executable, Main)
              When passed to the Eclipse executable, this option is used to locate the Java VM to use to run Eclipse. It
              should be the full file system path to an appropriate:  Java  jre/bin  directory,  Java  Executable,  Java
              shared  library  (libjvm.so),  or  a Java VM Execution Environment description file. If not specified, the
              Eclipse executable uses a search algorithm to locate a suitable VM. In  any  event,  the  executable  then
              passes the path to the actual VM used to Java Main using the -vm argument. Java Main then stores this val&#8208;
              ue in eclipse.vm.
..............
```you could use 
```
eclipse -vm <your jvm path>
```

I typed in that command into my terminal and I changed <your jvm path> to the path with my jdk, and to the path with my jvm. Eclipse opens up, and that same window pops up. :(

---

### Post by fdrake on 2011-08-05
> **WubiAR said:**
> I typed in that command into my terminal and I changed <your jvm path> to the path with my jdk, and to the path with my jvm. Eclipse opens up, and that same window pops up. :(

can you try to run the program from the terminal. Maybe it says more than that.

---

### Post by WubiAR on 2011-08-05
> **fdrake said:**
> can you try to run the program from the terminal. Maybe it says more than that.

I typed "eclipse" into the terminal and this is the output:
> /usr/share/themes/NOX/gtk-2.0/gtkrc:233: Murrine configuration option "gradients" is no longer supported and will be ignored.

Then comes the pop-up window:
> 
A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/usr/lib/eclipse/jre/bin/java
java in your current PATH


---

### Post by lkjoel on 2011-08-05
Could you give me the output of these commands?
```
ls /usr/lib/eclipse
ls /usr/lib/eclipse/jre
ls /usr/lib/eclipse/jre/bin
ls /usr/lib/eclipse/jre/bin/java

```

---

### Post by fdrake on 2011-08-05
this is funny because I have eclipse running with no problem and under 
/usr/lib/eclipse I don't have any jre folder.
```
 about_files  
artifacts.xml  
buildscripts  
configuration  
eclipse  
eclipse.ini  
features  
metadata  
p2  
plugins  
startup.jar

```

---

### Post by lkjoel on 2011-08-05
> **WubiAR said:**
> I typed "eclipse" into the terminal and this is the output:


Then comes the pop-up window:
Try this: [http://lkubuntu.wordpress.com/2011/07/12/upgrading-eclipse-to-3-7/](http://lkubuntu.wordpress.com/2011/07/12/upgrading-eclipse-to-3-7/)

---

### Post by WubiAR on 2011-08-05
This is really frustrating. I am going to remove it and then install it again. I'll report back the outcome.

---

### Post by YesWeCan on 2011-08-06
I uninstalled all OpenJava/Iced Tea stuff in synaptic.

I downloaded the JRE "compressed binary" from [http://www.oracle.com/technetwork/java/javase/downloads/java-se-jre-7-download-432155.html](http://www.oracle.com/technetwork/java/javase/downloads/java-se-jre-7-download-432155.html)

I copied it to /opt and extracted it
```
sudo tar zxvf jre-7-linux-x64.tar.gz
```

Then linked /usr/local/bin/java to it:
```
cd /usr/local/bin
sudo rm java
sudo ln -s /opt/jre1.7.0/bin/java .
```

Then linked the plugin to my Mozilla directory
```
cd /usr/lib/mozilla/plugins
sudo rm libnpjp2.so
sudo ln -s /opt/jre1.7.0/lib/amd64/libnpjp2.so .
```

Confirmed with: java -version
Went to [www.java.com](www.java.com) and clicked "Do I have Java?"

---

### Post by WubiAR on 2011-08-06
> **YesWeCan said:**
> I uninstalled all OpenJava/Iced Tea stuff in synaptic.

I downloaded the JRE "compressed binary" from [http://www.oracle.com/technetwork/java/javase/downloads/java-se-jre-7-download-432155.html](http://www.oracle.com/technetwork/java/javase/downloads/java-se-jre-7-download-432155.html)

I copied it to /opt and extracted it
sudo tar zxvf jre-7-linux-x64.tar.gz

Then linked /usr/local/bin/java to it:
cd /usr/local/bin
sudo rm java
sudo ln -s /opt/jre1.7.0/bin/java .

Then linked the plugin to my Mozilla directory
cd /usr/lib/mozilla/plugins
sudo rm libnpjp2.so
sudo ln -s /opt/jre1.7.0/lib/amd64/libnpjp2.so .

Confirmed with: java -version
Went to [www.java.com]("http://www.java.com") and clicked "Do I have Java?"

Should I follow what you wrote out as written? I tried to type in the exact same commands as you did (double checking that I downloaded the same file as you), and I keep getting errors when I execute them.

---

### Post by lkjoel on 2011-08-06
> **WubiAR said:**
> Should I follow what you wrote out as written? I tried to type in the exact same commands as you did (double checking that I downloaded the same file as you), and I keep getting errors when I execute them.
What are the errors?

---

### Post by YesWeCan on 2011-08-06
> **WubiAR said:**
> Should I follow what you wrote out as written? I tried to type in the exact same commands as you did (double checking that I downloaded the same file as you), and I keep getting errors when I execute them.
In theory those command should work as written. They did for me. I've put them in code tags to make them easier to read. Don't forget the . at the end of the ln commands.
If either of the rm commands fail that is ok - it just means the link isn't already there.

---

### Post by WubiAR on 2011-08-06
> **YesWeCan said:**
> In theory those command should work as written. They did for me. I've put them in code tags to make them easier to read. Don't forget the . at the end of the ln commands.
If either of the rm commands fail that is ok - it just means the link isn't already there.

YAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA!

Yes, it worked for me (after I learned a bit about cd,fwd, and pwd). Now, having got Java like this, will Eclipse work?

---

### Post by lkjoel on 2011-08-06
Try it!

---

### Post by WubiAR on 2011-08-06
> **lkjoel said:**
> Try it!

Awesome it worked. Thank you for your help, and thank you fdrake. A

ALSO, I am trying to run a HelloWorld.java file I made from the terminal, but I keep getting this error when I type in the command (I am in the working directory where the .java file is contained):

java HelloWorld.java

The output by the terminal:
> 
Error: Could not find or load main class HelloWorld.class


The code I have in the program:
> 
//comments
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}

//huge batch of comments down here, with the necessary /*, and */ statements 


---

### Post by lkjoel on 2011-08-06
Try javac HelloWorld.java, then java HelloWorld.

---

### Post by WubiAR on 2011-08-06
> **lkjoel said:**
> Try javac HelloWorld.java, then java HelloWorld.

Worked. Thank you very much. Problem solved.

---

### Post by YesWeCan on 2011-08-06
> **WubiAR said:**
> YAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA!

Yes, it worked for me (after I learned a bit about cd,fwd, and pwd). Now, having got Java like this, will Eclipse work?
Well done. :)
Don't forget to mark this as solved in [COLOR="Red"]Thread Tools[/COLOR].

---

