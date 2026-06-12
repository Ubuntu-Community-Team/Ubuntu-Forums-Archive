---
title: "problem with java intallation"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by dannydud on 2011-02-15
Hi,
I am very new to linux.I want to run my java programs in ubuntu.I hav ubuntu 9.10...
I typed the command 

sudo apt-get install openjdk-6-jdk

to download and install java.Then i wrote a simple hello program in editor and saved it as .java file.Then when i typed

javac hello.java

It says
 The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.3
 * jikes-classpath
 * jikes-kaffe
 * kaffe
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
javac: command not found

How can i make java program run in my system.Pls heip me out to fix the problem..

---

### Post by Mariane on 2011-02-15
Have you tried: 

javac ./hello.java

?

Mariane

---

### Post by dannydud on 2011-02-16
Yes i hav tried but it still says

The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.3
 * jikes-classpath
 * jikes-kaffe
 * kaffe
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
javac: command not found

Do i hav to install openjdk... again r do i hav to install anything else to make the programs work...?

---

### Post by lykeion on 2011-02-17
Try to update java alternatives. To list available alternatives:
```
update-java-alternatives -l
```
Then set alternative to OpenJDK:
```
sudo update-java-alternatives -s java-6-openjdk
```
This should update path to javac, test with:
```
which javac
```

---

### Post by gmargo on 2011-02-17
Looks like you do not have openjdk-6-jdk installed.  Double check with:
```

$ dpkg --get-selections | grep jdk
$ dpkg -L openjdk-6-jdk

```

---

### Post by dannydud on 2011-02-18
HI..

when i executed
sudo update-java-alternatives -s java-6-openjdk
 
it gave many update alternative error..

then when i executed
dpkg -L openjdk-6-jdk

it said
Package `openjdk-6-jdk' is not installed.

I guess java is not installed properly...i vil try installing it once again..

if i execute the command 
sudo apt-get install openjdk-6-jdk

java pakage vil be installed know?coz i did it this way last time..after that do i hav set any classpath to execute java programs..?can anyone pls give me steps to install n execute java programs...thanks in advance...

---

### Post by lykeion on 2011-02-18
You don't seem to have any JDK package installed. To install a JDK you could either start Synaptic or Ubuntu Software Center and search after "openjdk-6-jdk" or install directly in a terminal with this command:```
sudo apt-get install openjdk-6-jdk
```
With that installed you should be able to compile java source with *javac* command. If that doesn't help could you please paste any errors you get when trying to install (and please do enclose error output in code tags using the # button).

---

### Post by dannydud on 2011-02-20
Hi...
Thanks everyone.Java got installed properly & now its working fine.

---

### Post by dannydud on 2011-02-21
Hi..
I newly installed ubuntu to my laptop.when i tried to install java by the command
 
```
sudo apt-get install openjdk-6-jdk
```it worked fine 4 my desktop but i am getting error in my laptop..the errors r as below

#Reading package lists... Done
#Building dependency tree       
#Reading state information... Done
#You might want to run 'apt-get -f install' to correct these:
#The following packages have unmet dependencies:
 #openjdk-6-jdk : Depends: openjdk-6-jre (>= 6b20-1.9.5-0ubuntu1) but it is not going to be installed
 #               Recommends: libxt-dev but it is not going to be installed
 #sun-java6-jre : Depends: sun-java6-bin (>= 6.22-0ubuntu1~10.10) but it is not going to be installed or
 #                      ia32-sun-java6-bin (>= 6.22-0ubuntu1~10.10) but it is not installable
 #                Recommends: gsfonts-x11 but it is not going to be installed
#E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Then i tried

```
apt-get -f install
```Then it says

#E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
#E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I am the only user of my system..Then when i said "yes" in command line i get continous

y
y
y
y
.
.
.


So how can i slove this problem..Pls help..

---

### Post by Dutch70 on 2011-02-21
Oops double post, check the next one.

---

### Post by Dutch70 on 2011-02-21
You have to put "sudo" in front of the command to be root.

```
sudo apt-get -f install
```

But I'm curious...
 Why don't you just go to software center & install the Ubuntu restricted extras?

---

### Post by dannydud on 2011-02-21
Hi..
Thanks for the help..The code 
```
sudo apt-get -f install
```[FONT=monospace]worked..
now java is working fine..Thanks again..


[/FONT]

---

### Post by Dutch70 on 2011-02-21
> **dannydud said:**
> Hi..
Thanks for the help..The code 
```
sudo apt-get -f install
```[FONT=monospace]worked..
now java is working fine..Thanks again..
[/FONT]

You're welcome, glad it worked for you.
So this is solved?

---

