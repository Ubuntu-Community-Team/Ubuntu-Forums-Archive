---
title: "Setting PATH environment variable"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by eL7 on 2011-08-23
Greetings Ubuntards,
pretty new to linux but liking it so far.

Anyway since I've started I've found it kind of difficult to install software not found in the Software Center.

I was trying to download a programming IDE called JGrasp. I guess it's only accessible with Wine, but when I try to run it, it tells me this: 
[Unable to locate a java executable. Java 1.5 or igher must be installed to run jGrasp.
If Java is installed, you may beed to add the bin directory of the installation to your PATH environment variable.]

I've done this in Windows and searched about how to do it in Linux. A website told me I had to open this file in the terminal
"vi ~/.bash_profile"
and enter this
"export JAVA_HOME=<path>/bin/java"
"export PATH=$PATH:<path>/bin"

Well, not only do I not really know where the right path is, when I tried saving what I *thought* was the right information, I couldn't even figure out how to save the file. 

Other information: NetBeans works fine but I don't like it as much as jGrasp. I'm having problems downloading other programs but I'll just start with this.

Thanks,
eLseven

---

### Post by skatinjj on 2011-08-23
[http://ubuntuforums.org/showthread.php?t=44564](http://ubuntuforums.org/showthread.php?t=44564)

---

### Post by eL7 on 2011-08-23
> **skatinjj said:**
> [http://ubuntuforums.org/showthread.php?t=44564](http://ubuntuforums.org/showthread.php?t=44564)

Thanks for the quick reply. I followed that thread and the thread it linked to, and I was able to start jGrasp by using this comand in the terminal while in the right directory:
java -jar jgrasp.jar

This was said to be because Ununtu recognizes .jar files as .zip files instead of executable files, according to that thread.

So then what I'd like to know is how to create a Launcher for this program.

$ cd /home/<user>/Downloads/jgrasp/ java -jar jgrasp.jar


Thanks always,
eL7

---

### Post by llamabr on 2011-08-23
If by "launcher" you mean a button on the panel, then:

[https://help.ubuntu.com/community/HowToAddaLauncher](https://help.ubuntu.com/community/HowToAddaLauncher)

---

### Post by eL7 on 2011-08-24
Thanks. I found that page before I got your reply and it helped me out. I'm pretty new to scripting but it was successful. 

Now to spend some time on the forum...

Thanks,
7

---

### Post by lbarowski on 2011-08-24
Since it appears that java is on your PATH, you should be able to start jGRASP using the .../bin/jgrasp script. If that doesn't work, send us a bug report to let us know.

If you start with java -jar, the integrated Java debugger, interactions, and workbench won't work. To get full capability, you'll need:

java -classpath "jgrasp.jar:<java_home>/lib/tools.jar" Grasp

where <java_home> is the root directory of your Java installation.

---

