---
title: "How to download iTunes onto ubuntu?"
date: 2011-03-18
forum: New to Ubuntu
---

### Post by ichigo6420 on 2011-03-18
Hello, I saw this site that said I would be able to download itunes onto ubuntu,
[http://www.ehow.com/how_5197743_download-itunes-linux-ubuntu.html](http://www.ehow.com/how_5197743_download-itunes-linux-ubuntu.html)

I tried it, but I keep getting stuck at step four. this is what happens:

tumai@freegeek:~$ wine iTunesSetup.exe
wine: cannot find L"C:\\windows\\system32\\iTunesSetup.exe"
tumai@freegeek:~$ 

My version of ubuntu is 10.2 is that might help...

What do I do?

---

### Post by aysiu on 2011-03-18
That link is incorrect. iTunes does not run on Ubuntu.

---

### Post by milindo on 2011-03-18
> **ichigo6420 said:**
> 

My version of ubuntu is 10.2 is that might help...

That's not possible

---

### Post by tkelito on 2011-03-18
AFAIK you will not get iTunes to run properly under Wine. You may get it installed but it will not work correctly and Quicktime should throw a fit.

I haven't tried it since 9.10 and it didn't go smoothly nor did it work.


I suggest Rhythmbox or Banshee.  If you must have iTunes then your next step is Virtualbox+Windows+iTunes.  I unfortunately have to do this setup so that I can use LogMeIn for work.  It is the only task I can't perform in Ubuntu.

---

### Post by philipballew on 2011-03-18
the problem with installing itunes in ubuntu is with say wine or crossover you dont want to have unneeded apps installed and thats just what itunes does. if you open the .exe file in archive manager you'll see lots of msi files for different programs you dont nesserly need. what makes you want itunes more then some other software that you can sudo apt-get (software name) from the repos?

---

### Post by fcomstoc on 2011-03-18
I got an iPhone about a year ago and I spent many illustrating hours trying to figure out a way to sync with linux or install itunes to no avail. I finally just ended up rooting the phone so that I can transfer data and sync over ssh.

---

### Post by ichigo6420 on 2011-03-19
Oh okay thank you

---

