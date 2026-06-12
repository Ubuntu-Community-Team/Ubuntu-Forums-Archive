---
title: "Can't install Gmote - error message"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by Olivrwendl on 2010-08-01
I am still pretty new to Ubuntu. I am using 10.04 and I am having trouble installing gmote. I have downloaded and extracted the tar file. when I cut and paste the .sh command in the terminal this is the error message I get - 


teamha@TeamHA-desktop:~$ echo "Starting GmoteServer 2.0 ... "
Starting GmoteServer 2.0 ... 
teamha@TeamHA-desktop:~$ java -classpath bin:lib/jna.jar:lib/slf4j-api-1.5.3.jar:lib/swing-worker-1.2.jar org.gmote.server.GmoteServerUiLinux &
[1] 15438
teamha@TeamHA-desktop:~$ echo "GmoteServer started."Exception in thread "main" java.lang.NoClassDefFoundError: org/gmote/server/GmoteServerUiLinux
Caused by: java.lang.ClassNotFoundException: org.gmote.server.GmoteServerUiLinux
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: org.gmote.server.GmoteServerUiLinux. Program will exit.
teamha@TeamHA-desktop:~$ echo "GmoteServer started."

Any help would be appreciated.
Thanks,
Adam

---

### Post by gordintoronto on 2010-08-01
Don't cut and paste. CD to where the script is, then execute it. I'm not sure of the syntax, perhaps:
./GmoteServer

(Upper/lower case is important!)

---

### Post by orethrius on 2010-08-01
Per **gordintoronto**, it may be best to think of SH (shell script files) as BAT (batch file) equivalents.  Of course, you can get a general idea what a SH file will do by opening it as text; however, due to the nature of most logic-based commands, executing the lines independently of one another will only result in script failure, at best.

---

### Post by Olivrwendl on 2010-08-18
Thanks for for helping, but I am still not sure what to do. This is the only thing I have had trouble with using linux so far. I just can't seem to find a set of instructions anywhere for installing this application. How do I CD to where the script is and execute it? Sorry if this is a simple question, but any help is greatly appreciated.
Thanks

---

### Post by Olivrwendl on 2010-08-18
I figured it out - Thanks for your help
A

---

### Post by phroman on 2010-10-23
What was it??  I get command not found when trying to run the script.

---

### Post by insub2 on 2011-02-03
> **Olivrwendl said:**
> I figured it out - Thanks for your help
A

I'm glad to hear you figured it out. But I'd prefer to know how as I'm having the same problem and your solution probably would be helpful to me right now. ):P

---

### Post by Albatrossed on 2011-03-06
> **insub2 said:**
> I'm glad to hear you figured it out. But I'd prefer to know how as I'm having the same problem and your solution probably would be helpful to me right now. ):P


Same here. It's hard to find comprehensible instructions for running gmote in linux...!

---

### Post by Townley89 on 2011-05-05
My install of the server was pretty easy. In 11.04 you can just select "run" on the .sh file that you download from the gmote package. 

The trick for me was getting this "connection error". Turns out it's because I didn't have VLC installed.

---

