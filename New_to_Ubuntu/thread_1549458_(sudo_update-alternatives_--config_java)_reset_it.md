---
title: "(sudo update-alternatives --config java) reset it?"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by 13k on 2010-08-09
Just like the title says: How do i reset my java configurations?  Edit: I don't want any of the options from the menu... and for some reason, i can't run any of my .sh files.

---

### Post by jtarin on 2010-08-09
Why do you want to reset? What form of Java are you using? What menu are you referring too?

---

### Post by 13k on 2010-08-09
> **jtarin said:**
> Why do you want to reset? What form of Java are you using? What menu are you referring too?

 I can't run .sh files -.- ... sun java and openjdk... the menu from: sudo update-alternatives --config java after you installed java

---

### Post by jtarin on 2010-08-09
The file extension ".sh" is not a jave file extension.
Generally, .sh-scripts are Bourne Shell scripts or Bourne Again Shell scripts.

So long as a script has a proper shebang-line, you should be able to run them as follows:
```
chmod +x ShellScript.sh
./ShellScript.sh
```

The chmod only needs to be run once if the execute-flag isn't set. After the proper execute permissions have been set, they can be executed just like any normal executable. The shebang line* takes care of the executable that will interpret the file.

*The shebang line is the first line of the script, starting with a pound sign [ # ] and an exclamation mark [ ! ]. The shebang line is usually #!/bin/sh or #!/bin/bash, though it can also be (but is not limited to), for example, #!/usr/bin/perl or #!/usr/bin/python.

---

### Post by 13k on 2010-08-09
> **jtarin said:**
> The file extension &quot;.sh&quot; is not a jave file extension.
Generally, .sh-scripts are Bourne Shell scripts or Bourne Again Shell scripts.

So long as a script has a proper shebang-line, you should be able to run them as follows:
&quot;chmod +x ShellScript.sh
./ShellScript.sh[/CODE]The chmod only needs to be run once if the execute-flag isn't set. After the proper execute permissions have been set, they can be executed just like any normal executable. The shebang line* takes care of the executable that will interpret the file.

*The shebang line is the first line of the script, starting with a pound sign [ # ] and an exclamation mark [ ! ]. The shebang line is usually #!/bin/sh or #!/bin/bash, though it can also be (but is not limited to), for example, #!/usr/bin/perl or #!/usr/bin/python.

 ummm... ty?? i guess??... i already tried those commands, i even ran it in root x_x... =(... it said something about java...................................................................... &quot;chmod +x /home/xx/Starcraft/BWHFAgent/BWHFAgent.sh xx-xx-desktop:~$ sh /home/xx/Starcraft/BWHFAgent/BWHFAgent.sh Usage: java [-options] class [args...]            (to execute a class)    or  java [-options] -jar jarfile [args...]            (to execute a jar file)  where options include:     -d32          use a 32-bit data model if available      -d64          use a 64-bit data model if available     -client      to select the &quot;client&quot; VM     -server      to select the &quot;server&quot; VM     -hotspot      is a synonym for the &quot;client&quot; VM  [deprecated]                   The default VM is server,                    because you are running on a server-class machine.      -cp      -classpath                    A : separated list of directories, JAR archives,                   and ZIP archives to search for class files.     -D=                   set a system property     -verbose[:class|gc|jni]                   enable verbose output     -version      print product version and exit     -version:                   require the specified version to run     -showversion  print product version and continue     -jre-restrict-search | -jre-no-restrict-search                   include/exclude user private JREs in the version search     -? -help      print this help message     -X            print help on non-standard options     -ea[:...|:]     -enableassertions[:...|:]                   enable assertions     -da[:...|:]     -disableassertions[:...|:]                   disable assertions     -esa | -enablesystemassertions                   enable system assertions     -dsa | -disablesystemassertions                   disable system assertions     -agentlib:[=]                   load native agent library , e.g. -agentlib:hprof                     see also, -agentlib:jdwp=help and -agentlib:hprof=help     -agentpath:[=]                   load native agent library by full pathname     -javaagent:[=]                   load Java programming language agent, see java.lang.instrument     -splash:                   show splash screen with specified image&"

---

### Post by jtarin on 2010-08-09
I had problems running some java applications on my install and removed all iterations of Jave and installedFirst check if you have Java installed in your system. 
BWHF Agent requires the 32-bit version of Java 6.0 or higher. Type in a command window to check what version and if you have Java installed:

```
java -version
```

You can download and install Java [here:]("http://www.java.com/download") Get the self-extracting Linux version. **_Read the instructions._**

BWHF Agent requires the 32 bit version of java. If you installed the 64 version, please install the 32 bit version too, and if neccessary, edit the starter scripts to use the 32 bit version's java.exe and javaw.exe.

Another cause can be that even if you might have java installed in your system, the java.exe and the javaw.exe commands are not available because their folder is not in the execution path.

You can fix this in 2 ways:

    * You can add the java installation folder to your PATH environment. In fact you have to add the bin subfolder of it where actually the java exe files are located. [The PATH environment variable.]("http://www.cyberciti.biz/faq/linux-unix-set-java_home-path-variable/")

    * You can edit the BWHFAgent.cmd and BWHFAgent-console.cmd scripts, and add the full path of java.exe where it is installed. example "/usr/java/jre6/bin/java.exe" . 

Tip: you can check the value of the PATH environment variable by typing PATH in a command window.

---

### Post by 13k on 2010-08-09
> **jtarin said:**
> I had problems running some java applications on my install and removed all iterations of Jave and installedFirst check if you have Java installed in your system. 
BWHF Agent requires the 32-bit version of Java 6.0 or higher. Type in a command window to check what version and if you have Java installed:

```
java -version
```You can download and install Java [here:]("http://www.java.com/download") Get the self-extracting Linux version. **_Read the instructions._**

BWHF Agent requires the 32 bit version of java. If you installed the 64 version, please install the 32 bit version too, and if neccessary, edit the starter scripts to use the 32 bit version's java.exe and javaw.exe.

Another cause can be that even if you might have java installed in your system, the java.exe and the javaw.exe commands are not available because their folder is not in the execution path.

You can fix this in 2 ways:

    * You can add the java installation folder to your PATH environment. In fact you have to add the bin subfolder of it where actually the java exe files are located. [The PATH environment variable.]("http://www.cyberciti.biz/faq/linux-unix-set-java_home-path-variable/")

    * You can edit the BWHFAgent.cmd and BWHFAgent-console.cmd scripts, and add the full path of java.exe where it is installed. example &quot;/usr/java/jre6/bin/java.exe&quot; . 

Tip: you can check the value of the PATH environment variable by typing PATH in a command window.

  xx@xx-desktop:~$ java -version Usage: java [-options] class [args...]            (to execute a class)    or  java [-options] -jar jarfile [args...]            (to execute a jar file)  where options include:     -d32          use a 32-bit data model if available      -d64          use a 64-bit data model if available     -client      to select the &quot;client&quot; VM     -server      to select the &quot;server&quot; VM     -hotspot      is a synonym for the &quot;client&quot; VM  [deprecated]                   The default VM is server,                    because you are running on a server-class machine.      -cp      -classpath                    A : separated list of directories, JAR archives,                   and ZIP archives to search for class files.     -D=                   set a system property     -verbose[:class|gc|jni]                   enable verbose output     -version      print product version and exit     -version:                   require the specified version to run     -showversion  print product version and continue     -jre-restrict-search | -jre-no-restrict-search                   include/exclude user private JREs in the version search     -? -help      print this help message     -X            print help on non-standard options     -ea[:...|:]     -enableassertions[:...|:]                   enable assertions     -da[:...|:]     -disableassertions[:...|:]                   disable assertions     -esa | -enablesystemassertions                   enable system assertions     -dsa | -disablesystemassertions                   disable system assertions     -agentlib:[=]                   load native agent library , e.g. -agentlib:hprof                     see also, -agentlib:jdwp=help and -agentlib:hprof=help     -agentpath:[=]                   load native agent library by full pathname     -javaagent:[=]                   load Java programming language agent, see java.lang.instrument     -splash:                   show splash screen with specified image.......................... Can you explain this?

---

### Post by jtarin on 2010-08-09
No thanks. :)
[Let's do this another way.]("http://www.javatester.org/version.html")

---

### Post by 13k on 2010-08-10
> **jtarin said:**
> No thanks. :)
[Let's do this another way.]("http://www.javatester.org/version.html")

ehhhh thanks anyways... i reformated my computer -.- .... i could've ran runescape in my ubuntu 10.04 -.- ... but yeah.... o well :P

---

