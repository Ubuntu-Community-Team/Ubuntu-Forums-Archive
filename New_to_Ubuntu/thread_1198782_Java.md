---
title: "Java"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by cntrygrl17 on 2009-06-27
I have tried to install java i don't know how many times and it always fails!!! can someone help me plz?

---

### Post by nmccrina on 2009-06-27
What have you done so far?

Have you tried installing the package sun-java6-plugin through Synaptic? That'll give you the browser plugin, and will drag in the jre and stuff as dependencies. That should be all you need, unless you are trying to program Java.

---

### Post by QIII on 2009-06-28
In the terminal --

    sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-bin sun-java6-fonts sun-java6-jdk
    sudo update-java-alternatives -s java-6-sun

You may leave off sun-java6-jdk, if you wish.  That is the developers' kit.

When you are done, type

java -version and let us know what you get.

---

### Post by rockerphil on 2009-06-28
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
``` that should work if not just tell me i'm willing to help

edit: after you're done running this command and after you're done installing Java remember to restart Firefox (or whatever browser you use)

---

### Post by QIII on 2009-06-28
sudo update-java-alternatives -s java-6-sun  

Will make sure that Sun's JRE is the one selected by the OS if OpenJDK is also installed.

---

### Post by 3rdalbum on 2009-06-28
If you install Java using the terminal, when you get to the license agreement screen, you need to press the Tab key to select the "I Agree" button, and then the space bar or Enter to 'press' it.

---

### Post by picknick on 2009-06-28
Hi, I had  java 5 and now, thanks to your solution I got the 6.13, but when I enter to java.com and do the test to know my version it says that isn't the lastest.
I tried to install 6.14 downloading the package and installiang it manual (following tha instructions of given at the website) but seems like the system didn't recognize any change.

How can I do to install 6.14 from the terminal?
Should I change there were says java6 to java6_14 or something like that?
Here: 
>sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-bin sun-java6-fonts sun-java6-jdk
>sudo update-java-alternatives -s java-6-sun

Thanks,
Mariano.

---

### Post by QIII on 2009-06-28
You won't be able to install from the terminal, since what is in the repositories is Update 13.

You should be able to do anything you want with Update 13.

I haven't bothered to update, and I develop in Java...

---

### Post by picknick on 2009-06-28
Ok, I understand, what you get from apt-get command is what is in repositories. Good.

Thanks for the information and help!!!!!

Mariano

---

