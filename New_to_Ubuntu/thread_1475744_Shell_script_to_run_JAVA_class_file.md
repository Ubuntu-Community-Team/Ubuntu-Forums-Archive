---
title: "Shell script to run JAVA class file"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by siteregsam on 2010-05-07
Hi,

    I had written a shell script "run.sh" to invoke a java class file which in turn runs another shell file. My script file to run java class file is 

[COLOR=Blue][I]chmod +X 
#!/bin/bash 
java scr.java[/I][/COLOR]

and scr.java contains

[COLOR=Blue][I]import java.io.*;
import java.lang.Runtime;

public class scr
{
 public static void main(String[] args) 
  {
   try 
   {
     Process proc = Runtime.getRuntime().exec("/home/sam/Desktop/code/loadinfo.sh");
   }
   catch (Exception e) 
   {
     e.printStackTrace();
   }
  }
}[/I][/COLOR]

When i run run.sh i am getting following problem...

[COLOR=Red]sam@AcerAspire:~/Desktop/code$ ./run.sh
bash: ./run.sh: Permission denied[/COLOR]

What should i have to do to overcome the problem?  :confused:
Thanks in adv...

---

### Post by bredman on 2010-05-07
It looks like you do not have permission to execute run.sh. Use the command
ls -l run.sh
to check the permissions, post the result if you don't understand it. See also the next paragraph.

The command 'chmod +x' should not be in the script. This is the command to make the script executable, for example
chmod +x run.sh

If you run ls -l before and after chmod, you may see that the letter x appears in the second ls result, indicating that the script is now executable.

Do you really want to run the command 'java scr.java'? You need to compile the java file with the command javac to create a class file, then use the java command to load the class file.

Experiment with the commands from the command line before trying to put them into a script.

---

