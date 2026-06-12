---
title: "JAVA JRE not responding in Hardy - Need Help"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by UBuserCNVRG on 2009-01-28
I have gone through the threads to get Java JRE installed on Hardy.  Some really good information there for a beginner like me.  Unfortunately I have not been able to get it working.

Installed BIN file directly from SUN Java Website.

Used my terminal window to install.

Followed each instruction to the letter.

Went back to Java and tested the install.  It came back telling me I had jre-1.6.0.0  when I know the file was label 1.6.0_11

I am trying to use WEBEX on my laptap.

Any help would be greatly appreciated.

---

### Post by taurus on 2009-01-28
What's the output of this command from a terminal?

```
java -version
```

---

### Post by yeats on 2009-01-28
Java packages are available in the repositories.  Have you tried a search in Synaptic to see if a recent enough version is in there?

---

### Post by UBuserCNVRG on 2009-01-28
> **taurus said:**
> What's the output of this command from a terminal?

```
java -version
```



owner@owner-laptop:~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)

---

### Post by UBuserCNVRG on 2009-01-28
No I haven't.  The threads I was able to locate mentioned SUN java only.  I will give it a try

---

### Post by UBuserCNVRG on 2009-01-28
owner@owner-laptop:~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)

---

### Post by taurus on 2009-01-28
When you installed the new version by hand, where did you install it to (unpacked it)?  Do you see it from the output of this command?

```
sudo update-alternatives --config java
```

---

### Post by UBuserCNVRG on 2009-01-28
I installed the bin file in /usr/java.  I then unpacked it into /usr/lib/firefox/plugins

The output of that command is:

There is only 1 program which provides java
(/usr/lib/jvm/java-6-openjdk/jre/bin/java). Nothing to configure.

---

### Post by taurus on 2009-01-28
You unpacked the latest version of Sun's java in the plugin directory of firefox?  That is definitely a weird place to unpack it.  I would have unpacked it in /opt (or at least in /usr/lib/jvm) and then create a link from /usr/local/bin/java to point to the new version in /opt.

What are the outputs of these commands?

```
/usr/java -version
ls -la /usr/lib/firefox/plugins
```

---

### Post by UBuserCNVRG on 2009-01-28
I was simply following instruction from a thread I found.  I really didn't know where to put it.

Here is the output of those commands:

owner@owner-laptop:~$ /usr/java -version
bash: /usr/java: is a directory
owner@owner-laptop:~$ ls -la /usr/lib/firefox/plugins
total 8
drwxr-xr-x 2 root root 4096 2009-01-28 11:50 .
drwxr-xr-x 4 root root 4096 2008-11-12 18:51 ..
lrwxrwxrwx 1 root root   37 2008-12-21 15:09 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root   58 2009-01-28 11:50 libjavaplugin_oji.so -> /usr/java/jre1.6.0_11/plugin/i386/ns7/libjavaplugin_oji.so

---

### Post by taurus on 2009-01-28
Actually, looks like you unpacked it in /usr/java.  What's the output of this command from a terminal?

```
ls -la /usr/java/jre1.6.0_11
```

---

### Post by UBuserCNVRG on 2009-01-28
owner@owner-laptop:~$ ls -la /usr/java/jre1.6.0_11
total 300
drwxr-xr-x  8 root root   4096 2009-01-28 13:52 .
drwxr-xr-x  3 root root   4096 2009-01-28 13:54 ..
drwxr-xr-x  2 root root   4096 2009-01-28 13:52 bin
-r--r--r--  1 root root   3767 2008-11-10 01:54 COPYRIGHT
drwxr-xr-x  2 root root   4096 2009-01-28 13:52 javaws
drwxr-xr-x 18 root root   4096 2009-01-28 13:52 lib
-r--r--r--  1 root root  12601 2008-11-10 01:54 LICENSE
drwxr-xr-x  4 root root   4096 2009-01-28 13:52 man
drwxr-xr-x  4 root root   4096 2008-11-10 03:41 plugin
-r--r--r--  1 root root  15908 2008-11-10 01:54 README
drwxr-xr-x  2 root root   4096 2009-01-28 10:24 .systemPrefs
-r--r--r--  1 root root 228347 2008-11-10 01:54 THIRDPARTYLICENSEREADME.txt
-r--r--r--  1 root root    968 2008-11-10 01:54 Welcome.html

---

### Post by UBuserCNVRG on 2009-01-28
Hope this isnt getting too late in the day

---

### Post by bruce89 on 2009-01-28
I don't know if you can uninstall it easily, and then install *openjdk-6-jre* instead. Manual installation is a pain in the lower back region.

---

### Post by taurus on 2009-01-28
> **UBuserCNVRG said:**
> owner@owner-laptop:~$ ls -la /usr/java/jre1.6.0_11
total 300
drwxr-xr-x  8 root root   4096 2009-01-28 13:52 .
drwxr-xr-x  3 root root   4096 2009-01-28 13:54 ..
drwxr-xr-x  2 root root   4096 2009-01-28 13:52 bin
-r--r--r--  1 root root   3767 2008-11-10 01:54 COPYRIGHT
drwxr-xr-x  2 root root   4096 2009-01-28 13:52 javaws
drwxr-xr-x 18 root root   4096 2009-01-28 13:52 lib
-r--r--r--  1 root root  12601 2008-11-10 01:54 LICENSE
drwxr-xr-x  4 root root   4096 2009-01-28 13:52 man
drwxr-xr-x  4 root root   4096 2008-11-10 03:41 plugin
-r--r--r--  1 root root  15908 2008-11-10 01:54 README
drwxr-xr-x  2 root root   4096 2009-01-28 10:24 .systemPrefs
-r--r--r--  1 root root 228347 2008-11-10 01:54 THIRDPARTYLICENSEREADME.txt
-r--r--r--  1 root root    968 2008-11-10 01:54 Welcome.html

Try these.

```
sudo ln -s /usr/java/jre1.6.0_11/bin/java  /usr/local/bin/java
sudo update-alternatives --config java
```

---

### Post by UBuserCNVRG on 2009-01-29
owner@owner-laptop:~$ sudo ln -s /usr/java/jre1.6.0_11/bin/java  /usr/local/bin/java
ln: creating symbolic link `/usr/local/bin/java': File exists
owner@owner-laptop:~$ sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/jvm/java-6-openjdk/jre/bin/java). Nothing to configure.
owner@owner-laptop:~$

---

### Post by UBuserCNVRG on 2009-01-29
> **UBuserCNVRG said:**
> owner@owner-laptop:~$ sudo ln -s /usr/java/jre1.6.0_11/bin/java  /usr/local/bin/java
ln: creating symbolic link `/usr/local/bin/java': File exists
owner@owner-laptop:~$ sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/jvm/java-6-openjdk/jre/bin/java). Nothing to configure.
owner@owner-laptop:~$

taurus,  i really appreciate the help.  it got late yesterday.  here is the output from the commands you gave me.  Bruce89 suggested i unistall and run an automated install.  Your thoughts?

---

### Post by UBuserCNVRG on 2009-01-29
Bruce89, what's the best way to unistall?  Should I go back a couple of days and boot off of an earlier kernel?

---

### Post by jespdj on 2009-01-29
So, you just want to be able to use Java in Firefox. You're making it much more complicated than necessary.

Remove the stuff that you unpacked in the Firefox configuration directory. After that, install Sun Java 6 like this:
```
sudo apt-get install sun-java6-plugin
```

---

### Post by UBuserCNVRG on 2009-01-29
Thanks.  I am working on it now.

---

### Post by UBuserCNVRG on 2009-01-29
Any tips on removing non-empty directories...or is this my penance for doing it this way?

BTW  i tried apt-get remove program and got this response...and i tried this after I started deleting files..
root@owner-laptop:/usr/java/jre1.6.0_11# apt-get remove program
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package program

---

### Post by taurus on 2009-01-29
If you want to remove the version that you installed by hand, you can remove the whole thing from a terminal with

```
sudo rm -rf /usr/java
```
Also, look in /usr/local/bin and make sure to remove java in there if it points to the one that you have just removed.

```
sudo rm /usr/local/bin/java
```

---

### Post by UBuserCNVRG on 2009-01-29
Thanks taurus!

---

### Post by UBuserCNVRG on 2009-01-29
After I removed the old work I did the:

apt-get install sun-java6-plugin 

However, when I went to the Java web site to verify the install it still says that I am out of date 1.6.0_0 and need the 1.6.0_11 version.  BTW, WEBEX is still not loading

---

### Post by UBuserCNVRG on 2009-01-29
Completed the apt-get.  Tested java and got the message that I am using an older version.  What I am trying to do is load webex on Firefox so I can present over the web to my audience...webex is still not loading saying that java is not enabled in firefox...which I have checked and it is.

---

### Post by UBuserCNVRG on 2009-01-29
> **UBuserCNVRG said:**
> Completed the apt-get.  Tested java and got the message that I am using an older version.  What I am trying to do is load webex on Firefox so I can present over the web to my audience...webex is still not loading saying that java is not enabled in firefox...which I have checked and it is.

Perhaps I should reinstall firefox.  Any thoughts

---

### Post by UBuserCNVRG on 2009-01-29
I want to thank you all for your help to date.  Unfortunately, I am still unable to use java programs in firefox.  I know i have taken up more than my fair share of time, but if i don't get this fixed its back to windows for me...which i really would rather not do.  Any and all help is greatly appreciated.

If I can (as a sorce of repayment for the time spent) offer this Einstein quote I have on my wall "The main source of all technological achievements is the divine curiosity and the playful drive of tinkering and thoughtful research..." 

I am just trying to tinker my way into what I believe to be the truest form of computing...

---

### Post by UBuserCNVRG on 2009-01-30
Tauras, (et al)  Thank you again for your time.  Your 24 hour silence leads me to believe I need to do this on my own.  Again, thanks.  Soon to be MSuserCNVRG

---

