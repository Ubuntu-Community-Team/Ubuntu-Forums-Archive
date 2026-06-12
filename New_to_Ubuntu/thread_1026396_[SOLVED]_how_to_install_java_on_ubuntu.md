---
title: "[SOLVED] how to install java on ubuntu?"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by m.balakrishnan on 2008-12-31
how to install java on ubuntu?

---

### Post by mick222 on 2008-12-31
enable all sources exept for source and install ubuntu restricted extras from synaptic will install flash java and codecs for playing mp3 etc.
also look at sticky in multimedia section of forums.

---

### Post by greenleaves123 on 2008-12-31
Try reading my thread.

[http://ubuntuforums.org/showthread.php?t=1025225](http://ubuntuforums.org/showthread.php?t=1025225)

I had to uninstall and reinstall java several times. I am a newbie though, so I don't know if these instructions will work for you.

---

### Post by stevoo on 2008-12-31
> sudo apt-get install sun-java6-plugin
sudo apt-get install sun-java6-jre

enjoy

---

### Post by Michael.Godawski on 2008-12-31
hi, 

basically you either have to install ubuntu-restricted-extras
```
sudo apt-get install ubuntu-restricted-extras
```

which will install a bunch of useful stuff like codecs and java.etc.

or you install it separately with 
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by mick222 on 2008-12-31
Here's a link [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) just copy and paste the code there into terminal.
I notice you have a few posts on this please don't double post in future.

---

### Post by m.balakrishnan on 2008-12-31
ok thank u i am using this "***_sudo apt-get install ubuntu-restricted-extras_***" then after install how to open java? because i used notepad and command promt for java language in window xp,

---

### Post by sadaruwan12 on 2008-12-31
it's the same thing in ubuntu just use the Gedit text editor and the terminal

---

### Post by m.balakrishnan on 2008-12-31
i have no Gedit text editor [COLOR="Red"]**but can i use Winefish LaTeX editor?**[/COLOR] if it is not possible, how to get Gedit text editor

---

### Post by mick222 on 2008-12-31
Applications -> accessories -> text editor 
Gedit is part of Ubuntu by default.
Or install Eclipse from synaptic.

---

### Post by m.balakrishnan on 2008-12-31
thank you i got it.

---

### Post by m.balakrishnan on 2008-12-31
i wrote following program

[B][I]#import.java.io.*;
class bala
{
public static void main(String args[])IOException
{
 system.out.println("krishna");
}
}[/I][/B]

i could compile that program but while i run that program it shows follwing messange.

[B]"The program 'javac' can be found in the following packages:
 * jikes-sun
 * jikes-sablevm
 * gcj-4.2
 * kaffe
 * jikes-kaffe
 * java-gcj-compat-dev
 * ecj
 * j2sdk1.4
 * jikes-classpath
 * jikes-gij
 * gcj-4.1
 * sun-java5-jdk
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
bash: javac: command not found"
[/B]
[COLOR="Red"]**what will i do?**[/COLOR]

---

### Post by m.balakrishnan on 2008-12-31
i wrote the following program
[B][I]
#import.java.io.*;
class bala
{
public static void main(String args[])IOException
{
 system.out.println("krishna");
}
}[/I][/B]

[B]The program 'javac' can be found in the following packages:
 * jikes-sun
 * jikes-sablevm
 * gcj-4.2
 * kaffe
 * jikes-kaffe
 * java-gcj-compat-dev
 * ecj
 * j2sdk1.4
 * jikes-classpath
 * jikes-gij
 * gcj-4.1
 * sun-java5-jdk
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
bash: javac: command not found
[/B]
[COLOR="Red"]
what will i do?[/COLOR]

---

### Post by m.balakrishnan on 2008-12-31
i could compile that java program. but i can't run that java program.

---

