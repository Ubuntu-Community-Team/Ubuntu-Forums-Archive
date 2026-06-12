---
title: "samba broke"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by degarb on 2010-03-12
There is no system rewind, so I cannot get system back.

Woke up this morning and laptop cannot connect to windows network.  Isp is working fine.  I rebooted and my windows computer are invisible.

Now cannot do office on laptop, or watch movies with family (living room computer).  Etc.  Half functionality of machine, gone.

---

### Post by audiomick on 2010-03-12
There is a troubleshooting thread here
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by ikt on 2010-03-12
Do you have UFW running?

```
sudo apt-get install gufw
```

---

### Post by degarb on 2010-03-12
> **audiomick said:**
> There is a troubleshooting thread here
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

I just remembered, I set router to use open dns servers and fixed ip.   i must do this because twc seems to disconnect my modem every 200 name resolves or so.   And slow default servers. 


My windows machines are doing fine browsing the windows network, still.

I am now trying    name resolve order = lmhosts wins bcast host  ...restarted samba and still nothing.

 That page is a little daunting if you have a yelling wife and kids in background. 

(no idea what uwf is yet.)

---

### Post by degarb on 2010-03-12
> **degarb said:**
> I just remembered, I set router to use open dns servers and fixed ip.   i must do this because twc seems to disconnect my modem every 200 name resolves or so.   And slow default servers. 


My windows machines are doing fine browsing the windows network, still.

I am now trying    name resolve order = lmhosts wins bcast host  ...restarted samba and still nothing.

 That page is a little daunting if you have a yelling wife and kids in background. 

(no idea what uwf is yet.)

name resolve order = lmhosts wins bcast host

and a reboot fixed the issue!!

I hope in next version of Ubuntu, they really test more and work on the auto cd mounting/unmounting and the whole samba windows networking thing.

I do not get a sense of acomplishment after fixing and wrestling with these issues, rather a sense of disgust at loosing time. 

I will investigate trying to tweak, since I am not happy with how slow the linux machine lists shared files, compared with the xp machines.

---

### Post by degarb on 2010-03-12
> **ikt said:**
> Do you have UFW running?

```
sudo apt-get install gufw
```


I have yet to attempt firestarter or any firewall, since I know that will bring on a whole host of new technical challenges that will take time to solve.  Router has a firewall and we are talking linux.  I do bet when ubuntu reaches critical mass  some firewall will be needed.

Is gufw better than firestarter?  Wife yelling, "get off that machine!", easy?

---

### Post by theozzlives on 2010-03-12
> **ikt said:**
> Do you have UFW running?

```
sudo apt-get install gufw
```

How would a firewall help SAMBA connect to Windows?

> Now cannot do office on laptop, or watch movies with family (living room computer). Etc. Half functionality of machine, gone.

I had probs with Karmic after a update, I upgraded to Lucid to see if that would help... NOPE. I installed a fresh copy and still nope. There's just a bug that needs fixed.

---

### Post by ikt on 2010-03-13
> **theozzlives said:**
> How would a firewall help SAMBA connect to Windows?

Some people in the past have played around with UFW and it ends up blocking samba from connecting to anything.

---

### Post by degarb on 2010-03-13
> **theozzlives said:**
> How would a firewall help SAMBA connect to Windows?



I had probs with Karmic after a update, I upgraded to Lucid to see if that would help... NOPE. I installed a fresh copy and still nope. There's just a bug that needs fixed.

That trouble shooting page is helpful, but it lists several possible fixes.  I tried the first, not knowing if it would help.  It didn't then jumped to fix that seemed to match the opendns.com change bug, yes bug.  It worked.

I do feel this is bug, since changing a dns server on router shouldn't disable the windows shared folders, unless I can do some incantation on some file that fixes lookup order.

-------
I think there are 5 things Ubuntu needs to polish to make Ubuntu near perfect. 

The (1) windows networking and (2) cd automounting/unmounting needs some polishings. This is essential for most users.  Hoping by 10.4.

I feel the other two major holes in Ubuntu: (3) if no internet is autodetected after default wireless driver (any proprietary wireless card), then, please, wizard install gui of windows wrapper (since the gui of this is the easiest fix for new linux user). Also, on install, (4) most users would prefer to install Wine to run as many programs as possible. And so should be a wizard choice on install.  Then finally, I don't think option for  (5) enabling universal and multiverse repos, should be something only the forum lurkers should be privy.  Again, a wizard choice.     These 5 things fixed--or hurdles lowered by more clever means--, Ubuntu would be 99% "there" for the masses to use and overtake Windows usage.  Once a small critical mass gained, developers would be forced to write for Linux!  And, with Ubuntu success, all flavors of Linux would benefit with more compatibility and more programs.

---

### Post by degarb on 2010-03-13
> **ikt said:**
> Some people in the past have played around with UFW and it ends up blocking samba from connecting to anything.

Because you posted code for installing,  you implied that installing would help fix the networking.

I would edit your initial post.  I am interested reviews and impressions of this firewall, since I am a firewall believer.   AV, programs, oth, slow the system more than the typical virus or spyware, are often impossible to remove.  I just inherited a 5 year old perfectly working (seldom used/never used for testing sw/virus and spyware free) 1.6 ghz/512 ram desktop, that was discarded just because as AV have grown to such pigs in the last 5 years, the machine can no longer run smoothly, without crawling, with any installed av they tried.  So, I only feel AV should be used for download scanning, and occasional (av, trojan, spyware) scans if the system feels sluggish.  Also, I know, for a fact, they often over-flag legit virus-free programs (one's I wrote for my machine or others that worked for last 10 years and never got flagged), as virused, to keep their users paranoid.

---

