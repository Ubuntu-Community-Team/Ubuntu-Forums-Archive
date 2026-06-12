---
title: "java"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by Karlof on 2011-05-14
hi forum

I have just downloaded java jre-6u25-linux-i566.bin

in simple instructions how do i install it

the java in 10.10 software does not work for me

Thanks Karlof

---

### Post by sanderd17 on 2011-05-14
So you need the SUN JRE instead of the open JRE? Why don't you isntall it from the repo's?

[http://www.webupd8.org/2010/09/how-to-install-java-jre-and-java-plugin.html](http://www.webupd8.org/2010/09/how-to-install-java-jre-and-java-plugin.html)

---

### Post by thane1 on 2011-05-14
I agree with last poster.  I have one prog, which does not work with the open jre progs, but which works flawlessly with sunjava6 from the repos, once I then remove the open jre progs.

---

### Post by duke.tim on 2011-05-14
What they are saying is, open the software center type "java" and click install ^_^

---

### Post by Karlof on 2011-05-15
Hi 

I have not got JRE  java in my repositories on my 10.10 hence the download

I have JDK and iced tea but they do not work 

How do I get JRE java into my system

Thanks  Karlof

---

### Post by oldos2er on 2011-05-15
You need to enable the partner repository to install sun-java6-jre. [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories)

Or if you still want to install jre-6u25-linux-i566.bin, see [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by jrozo17 on 2011-05-15
[http://ubuntuforums.org/showthread.php?t=1758782](http://ubuntuforums.org/showthread.php?t=1758782)

Try looking at this, it should help. :)

---

### Post by cavalier911 on 2011-05-15
This .bin is a self-extracting binary archive.
Make a directory in /usr called java 
```
sudo mkdir /usr/java
```
Move jre-6u25-linux-i566.bin to /usr/java
```
sudo mv /*path.to.*/jre-6u25-linux-i566.bin /usr/java
```
Change directory to /usr/java
```
cd /usr/java
```
Change mode jre-6u25-linux-i566.bin to executable
```
sudo chmod a+x jre-6u25-linux-i566.bin
```
Extract jre-6u25-linux-i566.bin
```
./jre-6u25-linux-i566.bin
```

---

### Post by Karlof on 2011-05-15
hey forum

Thankyou all for a great response giving your help

I will read and digest and let you all know what happens


thanks again  karlof

---

### Post by slooksterpsv on 2011-05-15
Yeah here's what I have to do (techically I have a script to do all this for me =D):

Open Software Center -> Click on Edit -> Software Sources -> go to Other Software tab and click on the Checks for Canonical Partners

Next click on LXDE -> Accessories -> LXTerminal

Type in:

```

sudo apt-get update 
sudo apt-get install sun-java6-plugin
sudo update-java-alternatives -s java-6-sun

```
(When it prompts for password it won't show up, but it still keeps tab of what you type in)
That's how I get my sun java to work.

---

### Post by Karlof on 2011-05-17
Hi forum

I tried some of your suggestions I could not make them work I must be doing things wrong

However I upgraded to narwhal and I can use the java programme it has.

Thanks again for your interest and help

Karlof

P.S. are there any simple free ubuntu tutorials on  the web

---

### Post by manishraj2011 on 2011-05-17
> **Karlof said:**
> Hi forum

I tried some of your suggestions I could not make them work I must be doing things wrong

However I upgraded to narwhal and I can use the java programme it has.

Thanks again for your interest and help

Karlof

P.S. are there any simple free ubuntu tutorials on  the web
Try this

[http://ubuntuforums.org/showpost.php?p=10817674&postcount=22](http://ubuntuforums.org/showpost.php?p=10817674&postcount=22)

post back if you face any problem...

---

### Post by Karlof on 2011-05-21
Hi manishraj2011 and ohter contributers to this thread I could get java on narwhal 11.4 but the rest of narwhal is still very unstable, so I reloaded maverick 10.10 and followed sloopsterpsv formula in the terminal
and yes !!!!! java thanks guy's without your help we newbies would be lost

 CHEERS karlof

---

