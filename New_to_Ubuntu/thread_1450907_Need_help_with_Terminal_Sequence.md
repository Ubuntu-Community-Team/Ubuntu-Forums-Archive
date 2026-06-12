---
title: "Need help with Terminal Sequence"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by randl on 2010-04-09
Here is the sequence:
user@home:~$ INSTALL4J_JAVA_HOME=/usr/lib/jvm/java-6-sun/
user@home:~$ export INSTALL4J_JAVA_HOME
user@home:~$ mkdir thinkorswim
mkdir: cannot create directory `thinkorswim': File exists
user@home:~$ chmod 770 ./thinkorswim_installer.sh
user@home:~$ ./thinkorswim_installer.sh
[COLOR=Red]No suitable Java Virtual Machine could be found on your system.[/COLOR]
The version of the JVM must be at least 1.5.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
[COLOR=Red]You can also try to delete the JVM cache file /home/roberto/.install4j[/COLOR]
user@home:~$ rm /home/roberto/.install4j
rm: cannot remove `/home/roberto/.install4j': No such file or directory
user@home:~$ cd
user@home:~$ rm /home/roberto/.install4j
[COLOR=Red]rm: cannot remove `/home/roberto/.install4j': No such file or directory

[COLOR=Black]I am not sure how to approach this issue. I tried removing the file the system suggested to no avail.  The system still thinks it does not have a Java virtual machine.

Any suggestions?
randll
[/COLOR][/COLOR]

---

### Post by Shhnap on 2010-04-09
It sounds like you do not have the right version of java installed, have you tried:

```
sudo apt-get install java6-runtime java6-sdk
```

Then try the steps again.

Oh, and you do not need to run the exact same mkdir command twice. The file already exists.

And you can read the manual for the common commands by:

```
man <command>
```

In the terminal. 'q' quits. :)

---

### Post by randl on 2010-04-10
> **Shhnap said:**
> It sounds like you do not have the right version of java installed, have you tried:

```
sudo apt-get install java6-runtime java6-sdk
```Then try the steps again.

Oh, and you do not need to run the exact same mkdir command twice. The file already exists.

And you can read the manual for the common commands by:

```
man <command>
```In the terminal. 'q' quits. :)
-------------------------------------------0000000000--------------------------------------------------------
Thanks for the help I did as you suggested and it got me one step closer (I think?) to a solution except I hit another wall.  The script looks like this now:

**user@home**:~$ sudo apt-get install java6-runtime java6-sdk
[sudo] password for roberto: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package java6-runtime is a virtual package provided by:
  openjdk-6-jre 6b16-1.6.1-3ubuntu3
  sun-java6-jre 6-15-1 [Installed]
  default-jre 1.6-30ubuntu5
You should explicitly select one to install.
[COLOR=Red]E: Package java6-runtime has no installation candidate[/COLOR]
**user@home**:~$ INSTALL4J_JAVA_HOME=/usr/lib/jvm/java-6-sun/
**user@home**:~$ export INSTALL4J_JAVA_HOME
**user@home**:~$ chmod 770 ./thinkorswim_installer.sh
**user@home**:~$ ./thinkorswim_installer.sh
[COLOR=Red]No suitable Java Virtual Machine could be found on your system.[/COLOR]
The version of the JVM must be at least 1.5.
[COLOR=Red]Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.[/COLOR]
[COLOR=Red]You can also try to delete the JVM cache file /home/roberto/.install4j[/COLOR]

This is as far as I get,
randl

---

### Post by Shhnap on 2010-04-19
> You should explicitly select one to install.
E: Package java6-runtime has no installation candidate

That line is telling you what you are supposed to do. Pick a package in the list to install, for example:

```
sudo apt-get install sun-java6-jre
```

---

