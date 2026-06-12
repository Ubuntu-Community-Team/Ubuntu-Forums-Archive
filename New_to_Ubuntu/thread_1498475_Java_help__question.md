---
title: "Java help / question"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by RazzyDaz on 2010-05-31
I am looking for some help with Sun Java.  I have search the forum and have tried every suggestion, but nothing seems to fix the problems.  Let me first say, I think it's a java problem, or it may be Firefox.  Here is the problem:

[LIST=1]
[*] I'm trying to log into Logmein.com.  I can't seem to get past secure.logmein.com.  I am able to log in on Ubuntu 9.04 and 10.04 with no problems.  I really do not want to upgrade Ubuntu, unless it's absolutely necessary.
[*]Another problem is on Facebook. When I try to see who's online, it always gives me error and I have to refresh the page.  Also, the online people are no longer at the bottom right corner.  They are located on the side bar, off to the left.
[*]Trying to view a certain website, but the error says: javascrip: popup('chckctrl_46.asp')
[/LIST]
Any suggestion would be appreciated!

---

### Post by nhasian on 2010-05-31
by default the java in 10.04 is not from sun, its the open source java which sometimes has problems on some sites.  make sure your using sun's java instead.

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```


you can list the different javas on your computer with the command:

```
sudo update-java-alternatives -l
```

if necessary you can set it to sun's java with the command:

```
sudo update-java-alternatives -s java-6-sun
```

now run *java -version* to ensure that the correct version is being called.

---

### Post by RazzyDaz on 2010-05-31
```
sudo update-java-alternatives -l
```if necessary you can set it to sun's java with the command:

After inputing this, the output was java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun

I'm assuming this is the current Java.  I just don't understand why the previous and newer versions all work.  I'm more worried about getting Logemein to work, than Facbook.  I use Logmein for my business and can't seem to log in with this computer.  It basically stops at secure.logmein.com  Any ideas what may cause this?

---

### Post by frank002 on 2010-05-31
From your output, it seems you might have installed sun java without removing open djk. I think you have to remove one of them.

---

### Post by RazzyDaz on 2010-05-31
How do I remove the older version?  I am still trying to learn how to use Linux.  I love Linux, other than this issues!

---

### Post by lovinglinux on 2010-05-31
See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

