---
title: "FROSTWIRE and JAVA SUN"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-04-19
und
sh: unpack200: not found
sh: unpack200: not found
sh: unpack200: not found
HOSTNAME IS steve-desktop
Starting FrostWire...
Java exec not found in PATH, starting auto-search...
ls: cannot access /usr/lib/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
steve@steve-desktop:~$ 
I had the problem with JAVA SUN on my laptop and Taurus showed me the way.  I went back in the threads and tried to do it on my PC and this is where I am.  I have downloaded Frostwire, but can't find it and bungled the Sun Java download.    STUCK

---

### Post by Yed Ied on 2009-04-19
I'm sorry, Ubuntu 8.10- HP pavilion 1125- 80gig HD- 3.20GHz- Ubuntu is primary drive.

---

### Post by kamitsukai on 2009-04-19
silly question but do you have java installed?

***edit* never mind re-read you post...**

---

### Post by Wiebelhaus on 2009-04-19
First:

```
sudo apt-get remove sun-java6-jre
```

Then:

```
sudo apt-get install sun-java6-jre
```

---

### Post by Yed Ied on 2009-04-19
I ran 'sudo apt-get remove sun-java6-jre' the response was I needed to run 'dpkg --configure -a' then it asks for my superuser # and displays it then indicates 'bash: my number displayed: command not found'.  I'm showing an ERROR, red circle with a minus sign in it in the tool bar indicating 'ERROR:BrokenCount>O'This usually means that your installed packages have unmet dependencies'.  I'm sorry but I'm way over my head, I'll not touch anything till I hear from you. 
Thanks

---

### Post by Wiebelhaus on 2009-04-19
> **Yed Ied said:**
> I ran 'sudo apt-get remove sun-java6-jre' the response was I needed to run 'dpkg --configure -a' then it asks for my superuser # and displays it then indicates 'bash: my number displayed: command not found'.  I'm showing an ERROR, red circle with a minus sign in it in the tool bar indicating 'ERROR:BrokenCount>O'This usually means that your installed packages have unmet dependencies'.  I'm sorry but I'm way over my head, I'll not touch anything till I hear from you. 
Thanks

Open Synaptic Package Manager , find the Sun Java packages and try to remove them or repair them from there. After re-install with Synaptic.

Synaptic should take care of the dependencies for you.

---

### Post by Yed Ied on 2009-04-19
Synaptic Package Manager is covered with the ERROR window 'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct problem'.  E: _cache->open () failed, please report'.   I've gone into Terminal several times and run this 'dpkg' several times and instead of my superuser password not being shown it is displayed and I get 'the command not found'.  I can't get into Synaptic Package Manager.

---

### Post by Wiebelhaus on 2009-04-19
> **Yed Ied said:**
> Synaptic Package Manager is covered with the ERROR window 'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct problem'.  E: _cache->open () failed, please report'.   I've gone into Terminal several times and run this 'dpkg' several times and instead of my superuser password not being shown it is displayed and I get 'the command not found'.  I can't get into Synaptic Package Manager.

wth I don't understand.

You have ran:

```
sudo dpkg --configure -a
```

and it's revealing your password?


You should have this happen:

you have to type in ```
sudo dpkg --configure -a
```.As soon as the password will be asked for the login ```
[sudo] password for user:
``` you have to type your password, , you should not see the password repeated in the terminal window. Subsequently, the command will run or a complaint will be returned and will tell you what went wrong, asking you to re-enter the command.

---

### Post by Yed Ied on 2009-04-20
Processing triggers for man-db ...

Setting up unixodbc (2.2.11-16build2) ...

Processing triggers for libc6 ldconfig deferred processing now taking place

I don't know why but I did that several times last night and didn't get this message, but I still don't know what this means, please bear with me.

---

### Post by Yed Ied on 2009-04-20
I believe the fire is out.  As soon as I submitted my last post I noticed an indicator in the tool bar for downloads and it was Java.  I think PROBLEM SOLVED, thank you very much.

---

