---
title: "14 minutes deadline -- ubuntu 9.04 Vs ubuntu 8.04 Desktop"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by robertron76 on 2009-05-04
I'm downloading Ubuntu Desktop 9.04 as we speak, and I have Ubuntu 8.04 Desktop and Ubuntu 8.04 Server as CDs sent by Ubuntu.

So which one should I install?


[LIST]
[*]Ubuntu 9.04 Desktop
[*]Ubuntu 8.04 Desktop
[*]Ubuntu 8.04 Server
[/LIST]

I have a separate primary partition on my Windows Vista based laptop, I created for installing Ubuntu.

How easy would it be for me to upgrade to 9.04, later if I decide to go with 8.04 Desktop?

Any gotchas on installing either of this on a Windows Vista Ultimate 64-bit SP1, where I have a separate partition?

As this is a separate partition, can I install Ubuntu 8.04 and format the partition later and install Ubuntu 9.04, or should I upgrade from 8.04 to 9.04?

Pls reply me within 14 minutes, as I need to make a decision.

---

### Post by allenbradley on 2009-05-04
Go with 8.04. I'm running 9.04 right now, and so far, my system has hung at least 5 times. 8.04, on the other hand, runs like a charm. However, if you want Openoffice 3 and KDE 4.2 without enabling backports, go with 9.04.

---

### Post by tracerbullet on 2009-05-04
Go with 9.04.

Hey, you wanted an answer... :)

---

### Post by lindsay7 on 2009-05-04
I would install 9.04 unless you have an ATI graphics card.

---

### Post by Muffinabus on 2009-05-04
9.04, I didn't like 8.04 very much, my sound didn't work properly.

---

### Post by raymondh on 2009-05-04
If you go 8.04 and decide you want 9.04 ... you'll need to bump up to 8.10 first.  That or wipe out 8.04 and re-install 9.04

Folks have said "the latest is not always the greatest".  I have had good fortunes with 9.04

So .... why not try in live CD/Live session mode then decide? Either ubuntu will provide you with the means to be productive.  Also, consider separating your /home from /.

---

### Post by arashiko28 on 2009-05-04
9.04 it's very stable. Go for it, if you go for 8.04 and want to upgrade later, would have to do it by upgrading to 8.10 first and then 9.04.

Installation takes about 10-25 mins.

Nothing special, just be sure of the partition you're picking.

---

### Post by pbpersson on 2009-05-04
FYI, If you downloaded the server edition I do not think that has a GUI by default, you need to add it later from the command line.

I would not install the server edition if you want this to be a desktop

---

### Post by robertron76 on 2009-05-04
> **lindsay7 said:**
> I would install 9.04 unless you have an ATI graphics card.

I have an ATI graphics card.

Sounds like I should go for 9.04.

Anyways, lemme try 8.04 on this separate partition, and if didnt feel good, I'll format and install 9.04, thanks guys, that was freaking fast!!

---

### Post by TheNosh on 2009-05-04
> **raymondhenson said:**
> If you go 8.04 and decide you want 9.04 ... you'll need to bump up to 8.10 first.  That or wipe out 8.04 and re-install 9.04

Folks have said "the latest is not always the greatest".  I have had good fortunes with 9.04

So .... why not try in live CD/Live session mode then decide? Either ubuntu will provide you with the means to be productive.  Also, consider separating your /home from /.

good call on separating /home from /. that's how i've always done things :wink: 

i'd go with 9.04, it has newer packages, ext4, and the new notification system which i like (though some disagree)

---

### Post by kostkon on 2009-05-04
+1 from me for 9.04

---

### Post by robertron76 on 2009-05-04
> **robertron76 said:**
> I have an ATI graphics card.

Sounds like I should go for 9.04.

Anyways, lemme try 8.04 on this separate partition, and if didnt feel good, I'll format and install 9.04, thanks guys, that was freaking fast!!

And I do wanna install Desktop!!!!

---

### Post by zeroseven0183 on 2009-05-04
I suggest you install 9.04. You will still spend some time downloading the upgrades if you choose the earlier versions.

---

### Post by TheNosh on 2009-05-04
this doesn't effect your question at all, it's just to satisfy my own curiosity. but you're going with the gnome version (ubuntu) rather than kde (kubuntu) or xfce (xubuntu) right?

---

### Post by zeroseven0183 on 2009-05-04
> **robertron76 said:**
> And I do wanna install Desktop!!!!

Enjoy trying stuffs with Ubuntu. After all, it's Linux for human beings. :)

---

### Post by lindsay7 on 2009-05-05
Maybe you did not understand. There are problems with ATI cards and 9.04.  Look on this site for alot of detail on this subject.  8.10 has no problems with ATI as far as I have read.

---

### Post by robertron76 on 2009-05-05
Thanks everyone, I was able to install Ubuntu 8.04 from Live CD and started exploring it.

---

### Post by robertron76 on 2009-05-05
> **raymondhenson said:**
> Also, consider separating your /home from /.

Can you explain me further on this (how to do this and why etc), am total new to Unix as an OS Admin here, TIA!!!

---

### Post by raymondh on 2009-05-05
> **robertron76 said:**
> Can you explain me further on this (how to do this and why etc), am total new to Unix as an OS Admin here, TIA!!!

Robertron ....First the "WHY".... hoping my analogy works.  Am sure a staff or mederator or any forum member can/will explain better. Nevertheless, here goes:

Linux has a neat filing system where everything branches out from a main "directory" (which we'll call "/").    

On an ubuntu install, you have the option to install (partition) your home directory (known as /home) separate from the the "main directory".  The "home" directory is where we mostly, commonly store our personal data, media and files (i.e. files that we input INTO Ubuntu).

The advantages of having a separate /home partition is that should your ubuntu hiccup for any reason, your personal files (/home) are in a separate partition and thus spared the hiccup.  Another advantage is that should you need to do a fresh re-install, you can just then re-install over the "/" partition, which in effect, spares your personal files.

Now, this is not a back-up solution.  If your hard drive fails, you loose everything.  This is just to separate your files from ubuntu files. ALWAYS BACK-UP.  If this were windows, it'll be like having the system in C: drive while data and media is stored in a separate drive (F, G, W, X, whatever).

Here's a good read:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

This link is for IF YOU ALREADY HAVE UBUNTU INSTALLED.  If not, you can then manually separate the /home during the install process.  Do you have Ubuntu already installed?  Let me know if you need the "let's-start-from-the-beginning-I-have-no-ubuntu-installed" :)

EDIT : Googling with my best google-fu, I came up with some more links for you to read. Am at work but will come back in about 5 hrs.  Will gladly try to guide you.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://welcometoubuntu.blogspot.com/2008/02/how-to-install-ubuntu-710-with-separate.html](http://welcometoubuntu.blogspot.com/2008/02/how-to-install-ubuntu-710-with-separate.html)
[http://beginlinux.com/desktop_training/ubuntu/1073-ubuntu-intrepid-ibex-install](http://beginlinux.com/desktop_training/ubuntu/1073-ubuntu-intrepid-ibex-install)

(though for 7.10 and Ibex, I believe the process is still the same)


Enjoy the learning and welcome to linux and Ubuntu.

---

### Post by mariane_08 on 2009-05-05
> **lindsay7 said:**
> Maybe you did not understand. There are problems with ATI cards and 9.04.  Look on this site for alot of detail on this subject.  8.10 has no problems with ATI as far as I have read.

Hmmm I've been wondering about upgrading to 9.0 but decided to wait a few weeks so bugs get ironed out. 

I have an ATI graphics card and generally on 8.04 its OK but not everything though. I have a problem viewing very large PDF's which are graphically intensive and the system freezes up. From what I am learning this seems to be related to ATI cards (a driver issue perhaps?) I'm still trying to resolve it.

I hope the problem with ATI in 9.04 get resolved so I have the option of upgrading when I choose. Can someone tell me exactly what the ATI problems are in 9.04? related to my one above perhaps?

---

### Post by raymondh on 2009-05-05
> **mariane_08 said:**
> Hmmm I've been wondering about upgrading to 9.0 but decided to wait a few weeks so bugs get ironed out. 

I have an ATI graphics card and generally on 8.04 its OK but not everything though. I have a problem viewing very large PDF's which are graphically intensive and the system freezes up. From what I am learning this seems to be related to ATI cards (a driver issue perhaps?) I'm still trying to resolve it.


Mariane ... I did read some launchpad issues about the ATI card.  This is my experience. I have a HD2600XT card with a 9.04 and ext4 install on my desktop.  I have had no problems.  I may be lucky or the gods may be smiling temporarily at my install :)  Granted, I may only have been hashing GIMP a lot (and some videos and a couple of large PDF's) but .... I have had no problems on card capabilities with 9.04.... no freeze nor hangs.

Now, on my little wind, it's the wifi and that darned realtek 8187 that's giving me problems.:)  Oh well.

Have fun

---

### Post by zimmerj on 2009-05-06
There are also problems with 9.04 who have intel graphics cards.  Depending on the chipset, there are a number of cases in which a hard boot is required.  check out: 

[https://wiki.ubuntu.com/X/Bugs/IntelDriver](https://wiki.ubuntu.com/X/Bugs/IntelDriver)

I just upgraded from 8.10 to 9.04 and have experienced many crashes which I did not encounter before.

---

