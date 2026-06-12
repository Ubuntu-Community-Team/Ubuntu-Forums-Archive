---
title: "Problem openning a .sh file"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by Radissthor on 2009-10-14
Ok I post this here because I know it's so basic you wouldn't believe, but! as I have said y numerous parts of this forums, I'm a total and comp&#314;ete newbie.

So here's the thing. I downloaded a .sh file. I double clicked and an error appears that reads:
Could not open the file /home/hernan/impro-visor_unix_4_07.sh. 
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.
 
So I read some posts and I double cliked on the file, went to properties>permissions and I clicked where it said "allow executing file as program". When I did that, I got 4 options:
Run in Terminal, Display, Cancel, Run
Run in Terminal and Run don't produce anything
Display gives me the same error
well, obviously cancel is not an option

I also tried running the file through the terminal with the following command:
bash impro-visor_unix_4_07.sh (impro-visor_unix_4_07.sh is the name of the file)
and the result was:
No suitable Java Virtual Machine could be found on your system.
The version of the JVM must be at least 1.5.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
You can also try to delete the JVM cache file /home/hernan/.install4j

Any help, please?

---

### Post by dearingj on 2009-10-14
Have you installed a Java interpreter on your system? Open up Synaptic (System->Administration->Synaptic Package Manager) and search for packages with 'openjdk' or 'sun-java' or 'gcj-jre' in their names and see if any of them are installed. If none are, then I'd recommend installing sun-java6-jre.

---

### Post by Radissthor on 2009-10-14
Yes, it worked. I typed "openjdk" and installed the first icon, which included a 100 files!!! But I downloaded them all (it was something like 36 mb) and now the file could run on the terminal and it is installed. 
Thank you very much!:)

---

