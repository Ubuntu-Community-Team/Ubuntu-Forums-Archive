---
title: "Problems installing Java"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by mosquetero on 2009-02-20
Hi everyone!

I am using the last version of the standard Ubuntu and I am trying to install the lastest Java. In the Java's website it says clearly how to install it and I follow all the steps without any problem, but eventually it doesn't work. Does anyone know what can be happening? (I have Mozilla Firefox 3.0.5)

Thanks

---

### Post by taurus on 2009-02-20
What steps did you do to install it by hand, from a terminal?

There is a version from the repos if you want to install it with either add/remove, synaptic, or apt-get.

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by mosquetero on 2009-02-22
Thanks! It worked :D

---

### Post by snaggapuss on 2009-02-22
Having problems with Java myself, I did the apt get etc but that just downloads version 6u10 which doesn't do what I want it to, I downloaded 6u12 followed instructions on java page, onluy to get
Extracting...
./jre-6u12-linux-i586-rpm.bin: 365: ./install.sfx.10410: not found.

All i'm trying to do is to get the jave plugins to work on firefox so i can play online.  Its a new sytem, dual core Intel 5800, with the 64bit ubuntu programe. Its hard to decide whether or not to change to the 32 bit download as I'm a bit of a noob with linux. Any help apreciated

---

### Post by mosquetero on 2009-02-22
It is quite strange snaggapuss... I followed the instructions of the Java's website and I got not problems at all (later it didn't work until I wrote what taurus said). Make sure you are in the folder where the .bin is when you execute the chmod command. Which step you get stuck in?

---

### Post by karlr42 on 2009-02-22
Just use the version in the repos, with the above apt-get command. It will take no time, and you won't have to do anything else.

---

### Post by newbeeman on 2009-02-22
> **karlr42 said:**
> Just use the version in the repos, with the above apt-get command. It will take no time, and you won't have to do anything else.

Seems there are a number with Java problems, I'm another one.
The Java I have previously installed from synaptic are old. I need a newer version to run Pogo.
Went to the Java site, downloaded the latest to my desktop, but don't have enough experience to install from the terminal.
Can someone help, please.:(

---

### Post by txcrackers on 2009-02-22
This is actually much easier than y'all are making it - just install the Java 6 packages mentioned above. Do **not** download and try to install from the Sun website unless you already know what you're doing - it's a bit convoluted and will only leave you frustrated.

From a user's point of view, there is practically **zero** difference between 1.6.0_10 and 1.6.0_14 - you will not see or necessarily benefit from the bug-fixes between these two releases.

I'm a very long-time Java pro and I'm perfectly content with the version in the repositories. If you're having problems with Java applications and you've followed the above instructions, the problem is **not** that you don't have the latest *bugfix* release.

---

