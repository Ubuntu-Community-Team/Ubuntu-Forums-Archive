---
title: "Biometric Weight Manager"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by BillyBusBrown on 2009-03-22
I was looking for a program to record and manage information about my exercise habits, and Biometric Weight Manager looks like a very nifty program.

I download it from [http://www.bioweblogic.com/products/bwm20/]("http://www.bioweblogic.com/products/bwm20/"), its a tar.bz2 file, so I un tar.bz2 it and look at the install.linux file

> 1. Install java runtime (version 1.5+ or higher required).

2. Set JAVA_HOME pointing to correct path.

3. Unzip package and locate "jbwmdesktop\bin\jbwmdesktop" script, launch .

I have java installed.  I don't know what the jazz about the correct path means but I hoped my path was correct or whatever.  but when I ran the script a neat little menu comes up with a progress bar, the progress bar goes about halfway through and it closes. No error messages, and if I run it in the terminal nothing gets written to the screen.

how do I get it to work?

---

### Post by Xiong Chiamiov on 2009-03-23
You can check what JAVA_HOME is set to with the command
```

echo $JAVA_HOME

```
It's probably set correctly since it runs, but it's worth checking.

---

### Post by BillyBusBrown on 2009-03-23
when I use the command "echo $JAVA_HOME" I get a big blank after the command in the terminal and nothing else.

"whereis java" yeilds 
/usr/bin/java /etc/java /usr/lib/java /usr/share/java

---

