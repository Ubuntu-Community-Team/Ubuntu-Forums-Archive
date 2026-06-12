---
title: "Error invoking a shell script from a java program"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by siteregsam on 2010-04-18
Hi,

  I am trying to invoke a shell script file in a java program. The shell script file 'loadinfo.sh' contains

[COLOR=Blue]#!/bin/bash +x

echo DATE':' > loadinfo.txt
date >> loadinfo.txt

echo \ >> loadinfo.txt
echo CPU USAGE INFO':' >> loadinfo.txt 
cat /proc/stat >> loadinfo.txt

echo \ >> loadinfo.txt
echo MEMORY USAGE INFO':' >> loadinfo.txt 
cat /proc/meminfo >> loadinfo.txt[/COLOR]
And my java program that invokes 'loadinfo.sh' is

[COLOR=Blue]import java.io.*;
import java.lang.Runtime;

public class scr {

   public static void main(String[] args) {
      
       //Process proc = null;
       try {
           Process proc = Runtime.getRuntime().exec("hello.sh");
       } 
       catch (Exception e) {
        e.printStackTrace();
       }
   }
}[/COLOR]
When i execute the java file i am getting following error

sam@AcerAspire:~/Desktop/code$ java scr
[COLOR=Red]java.io.IOException: Cannot run program "hello.sh": java.io.IOException: error=2, No such file or directory
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:474)
    at java.lang.Runtime.exec(Runtime.java:610)
    at java.lang.Runtime.exec(Runtime.java:448)
    at java.lang.Runtime.exec(Runtime.java:345)
    at scr.main(scr.java:10)
Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
    at java.lang.UNIXProcess.<init>(UNIXProcess.java:164)
    at java.lang.ProcessImpl.start(ProcessImpl.java:81)
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:467)
    ... 4 more

:confused:[/COLOR]
Someone kindly help me to solve this problem, thanks in advance.

---

### Post by Bachstelze on 2010-04-18
In your Java program, put the absolute path to your shell script instead of just its name.

---

### Post by siteregsam on 2010-04-18
[COLOR=Black]Problem Solved,
Thanks[/COLOR][COLOR=Black] Bachstelze :)

[/COLOR]

---

