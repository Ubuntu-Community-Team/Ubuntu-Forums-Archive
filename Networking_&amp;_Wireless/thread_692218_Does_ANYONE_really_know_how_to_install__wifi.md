---
title: "Does ANYONE really know how to install  wifi?"
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by BillB on 2008-02-09
I just went through a 3 day ordeal (here), trying to install a wireless adapter....in the end, NOTHING.

My Ubuntu 7.10 laptop sees the card, I downloaded it's XP driver & the TWWWGPC_Temp directory files (.inf & .sys), I installed ndiswrapper (common & utils), and many many lines of commands.  NOTHING....I'm no closer to Network acknowledging wifi, than landing on the dark side of the moon!

Does ANYONE (really) know what there doing, installing wifi on Linux (Ubuntu)?
Is there a procedure that works?

---

### Post by woedend on 2008-02-09
what card do you have?

---

### Post by bwhite82 on 2008-02-09
Gotta start with the simple first. Do you have a chassis switch on your computer to enable wireless? If so, try pressing it. I've ran into the same problem as you in the past, and in the end it was because wireless was off by default. I was so frustrated, I could have cried.

---

### Post by rucadulu on 2008-02-09
Not to sound like I am promoting another distro, but, I have noticed that some wifi cards just will not work under Ubuntu or are so difficult to get working that it makes you wonder if it is really worth the hassle. When I have encountered this, I trying using PClinuxOS as an alternative to Ubuntu and about 75% of the time it will pick up wifi cards that ubuntu will not. Another good distro for wifi cards which is based off of Ubuntu is SimplyMEPIS. You may want to give either of these two a try and see if you have more luck.

---

### Post by BillB on 2008-02-09
It's a 2Wire PCMIA adapter in a Dell CPX laptop....card worked in laptop w/ XP, till it crashed (nothing to do w/ the card).  I didn't use any switch?

People here have got this card to work....but it sounds conflicting to me (beginner).

Is there any basic method to wifi?

---

### Post by jfinkels on 2008-02-09
> **BillB said:**
> It's a 2Wire PCMIA adapter in a Dell CPX laptop....card worked in laptop w/ XP, till it crashed (nothing to do w/ the card).  I didn't use any switch?

People here have got this card to work....but it sounds conflicting to me (beginner).

Is there any basic method to wifi?

The general method is to install the driver and start surfing the tubes.

The specific method is unique to each hardware combination. There may be some special work-around for your particular card. 

Take a look here for a compilation of howtos and specific instructions for particular cards: [https://help.ubuntu.com/community/WifiDocs/](https://help.ubuntu.com/community/WifiDocs/)

Can you post the output of the following command so that we can see the specific make and model of your card:```
lspci -v
```

---

### Post by Hightide on 2008-02-09
Hi BillB

Soldierboy has a point, sometimes newer laptops come with features to disable the wireless radio to save the battery when not in use.

You could rule this out by using the command

lshw

and checking at the end of the output  if it states ** *-network DISABLED or wireless=radio off**, that could be our problem.

regards

:)

---

### Post by BillB on 2008-02-09
> **Hightide said:**
> Hi BillB

Soldierboy has a point, sometimes newer laptops come with features to disable the wireless radio to save the battery when not in use.

You could rule this out by using the command

lshw

and checking at the end of the output  if it states ** *-network DISABLED or wireless=radio off**, that could be our problem.

regards

:)

This isn't a newer laptop, it's an old Dell CPX -J, 650MHz P3.  Does/can Ubuntu turn off the wifi?
Like I said, I had no problems w/ Windows 98SE or XP.

---

### Post by kevdog on 2008-02-09
this will give you same basics, and then let's talk, the lack of any info here is driving me nuts!
[http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)

---

### Post by BillB on 2008-02-09
> **BillB said:**
> This isn't a newer laptop, it's an old Dell CPX -J, 650MHz P3.  Does/can Ubuntu turn off the wifi?
Like I said, I had no problems w/ Windows 98SE or XP.

Well your right!

lshw shows that the *-network DISABLED   It also says in the last line, wireless = NOT READY.

But what do I do to enable it?  I've never seen a "switch"?

It's an Intersil ISL 3886 card (I knew that)....(Prisim Javelin/Prisim Xbow) (rev 01)


I googled the chipset - 
Prism XBow 11abg CardBus - Mini - PCI WLAN

---

### Post by bwhite82 on 2008-02-09
Is it a "soft switch", ie you have to do a key combonation (like on my laptop Fn+F2)?

---

### Post by kevdog on 2008-02-09
Does lshw -C network report a driver being used or is it UNCLAIMED = no driver installed

---

### Post by BillB on 2008-02-09
> **kevdog said:**
> Does lshw -C network report a driver being used or is it UNCLAIMED = no driver installed

lshw -C network, shows *-network DISALED.

I posted the chip set on page 1.

---

### Post by kevdog on 2008-02-09
Is a driver assigned?

What if you type
sudo ifconfig <interface> up

where <interface> might be wlan0, eth1, etc

---

### Post by BillB on 2008-02-09
Does anyone know how to 'soft switch' the NETWORK on?  Dell CPX.  Fn + F2 didn't work (unless I need to boot?)

---

### Post by BillB on 2008-02-09
> **kevdog said:**
> Is a driver assigned?

What if you type
sudo ifconfig <interface> up

where <interface> might be wlan0, eth1, etc

sudo ifconfig says, UP = Loopback Running, MTV:16436, Metric:1

---

### Post by kevdog on 2008-02-09
If you could post some of the output it would be great.

---

### Post by BillB on 2008-02-09
> **kevdog said:**
> If you could post some of the output it would be great.

I don't know how to copy from my Ubuntu laptop, w/o internet....and paste to this PC w/ a connection. (I'm asked that a couple times a day).

There was nothing like wlan0 or eth1.   What else do you want to know from that screen?

I'm just trying to get the "switch' from DISABLED to enabled....and can't find anyone who knows how to do that on a Dell?  (I started another post, just for that!)

---

### Post by BillB on 2008-02-10
> **kevdog said:**
> If you could post some of the output it would be great.

kevdog,

I got something with sudo iwconfig -

lo,             no wireless extension

eth0,         NOT READY  ESSID : off/any


The rest was jusy nothing happening, if you know what I mean?

Hope this helps?

---

### Post by BillB on 2008-02-11
OK....if knowone knows the the best process to install wifi w/ my adapter on Ubuntu, is it any easier in Kubuntu or Xubuntu?

P.S.  I can't even find someone who can tell me how to "switch" on radio/wireless on my Dell CPX!

---

### Post by jfinkels on 2008-02-11
It looks like some other people have used ndiswrapper (a Linux program that allows you to install Windows drivers for your wireless card) successfully to get this card working. See [here](http://ubuntuforums.org/archive/index.php/t-600309.html), [here](http://ubuntuforums.org/showthread.php?t=35949), and [here](http://www.nin.knaw.nl/~heimel/computers/connecting_wireless.html), for example.

What you need to do is (1) install ndiswrapper:```
sudo aptitude install ndiswrapper
```

(2) download the Windows driver (or copy it from a disc, if you have a driver disc; if you don't have a disc, you'll need to search around using Google or something like that),

(3) install the driver using ndiswrapper by doing something like:```
sudo ndiswrapper -i PRISMDRIVER.inf
```

and (4) install the ndiswrapper module [into the kernel] by typing:```
sudo modprobe ndiswrapper
```

Of course, this may not work for you! You may need to do some more reading, you may need to blacklist an older, automatically installed prism driver by adding the line "blacklist prism54" or something like that to /etc/modprobe.d/blacklist.

---

### Post by BillB on 2008-02-11
> **jfinkels said:**
> It looks like some other people have used ndiswrapper (a Linux program that allows you to install Windows drivers for your wireless card) successfully to get this card working. See [here](http://ubuntuforums.org/archive/index.php/t-600309.html), [here](http://ubuntuforums.org/showthread.php?t=35949), and [here](http://www.nin.knaw.nl/~heimel/computers/connecting_wireless.html), for example.

What you need to do is (1) install ndiswrapper:```
sudo aptitude install ndiswrapper
```

(2) download the Windows driver (or copy it from a disc, if you have a driver disc; if you don't have a disc, you'll need to search around using Google or something like that),

(3) install the driver using ndiswrapper by doing something like:```
sudo ndiswrapper -i PRISMDRIVER.inf
```

and (4) install the ndiswrapper module [into the kernel] by typing:```
sudo modprobe ndiswrapper
```

Of course, this may not work for you! You may need to do some more reading, you may need to blacklist an older, automatically installed prism driver by adding the line "blacklist prism54" or something like that to /etc/modprobe.d/blacklist.


jfinkels,

(1)
"sudo aptitude install ndiswrapper" did not work.
It says "couldn't find package".  But did find ndiswrapper - common, modules-1.9, and utls -1.9.
No packages were installed.

?

(2)
I already have the driver information on Ubuntu

(3)
I have P54 & P54 common, and WlanUIG.info & WlanUIG.sys files?


I really can't understand much of the 3 other explanations/posts that you sent me, as I'm a beginner.   I was hoping someone, who know linux much better than I (less than a week w/ Ubuntu) could read them and come up with the best way to proceed with this?  Line for line so I don't make any mistakes, using* one *method.

---

### Post by JoJoArmani on 2008-02-11
Bill I understand your pain! Think I'm gonna give up and try one of those other os that a prev person mentioned. My card is also disabled from originally being "on" but without a connection. I don't even get any output from the card when I do those comands - so at least yours is kind of alive!

Good luck mate!!!:)

---

### Post by jfinkels on 2008-02-11
Read the first link in my signature, "Installing software".

> **BillB said:**
> jfinkels,

(1)
"sudo aptitude install ndiswrapper" did not work.
It says "couldn't find package".  But did find ndiswrapper - common, modules-1.9, and utls -1.9.
No packages were installed.

?

Oops, my bad! To install ndiswrapper, follow the instructions [here](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper). That site will also give you a general method for installing drivers using ndiswrapper.
> 

(2)
I already have the driver information on Ubuntu

If by "information", you mean ".inf files" or at least a .exe file, then good! Now follow the instructions on the page to which I linked above, because it seems you want a general guide like that one.

In general, though, you will not always get a universal, all-purpose setup guide. Everyone has different hardware/software combinations.

You might want to try the program "ndisgtk", which 

The high-level description for using ndiswrapper is this:
(1) install ndiswrapper
(2) obtain the .inf file (the windows driver file)
(3) install the .inf file using ndiswrapper

---

### Post by BillB on 2008-02-11
> **jfinkels said:**
> Read the first link in my signature, "Installing software".


Oops, my bad! To install ndiswrapper, follow the instructions [here](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper). That site will also give you a general method for installing drivers using ndiswrapper.

If by "information", you mean ".inf files" or at least a .exe file, then good! Now follow the instructions on the page to which I linked above, because it seems you want a general guide like that one.

In general, though, you will not always get a universal, all-purpose setup guide. Everyone has different hardware/software combinations.

You might want to try the program "ndisgtk", which 

The high-level description for using ndiswrapper is this:
(1) install ndiswrapper
(2) obtain the .inf file (the windows driver file)
(3) install the .inf file using ndiswrapper


I ALREADY HAVE NDISWRAPPER IN SYMPTIC PACKAGE MANAGER.

It's obvious KNOWONE here knows what they are doing!

---

### Post by jfinkels on 2008-02-11
BillB, I apologize for misunderstanding your communications within this thread. If you have already installed ndiswrapper, used ndiswrapper to install the .inf file, etc. and you still cannot access the internet, I'm not sure that I can help you further. Again, the members of this forum are not all experts, paid for technical support or something like that; we are all users, just like you! The best I can do is show you what I know, and this is it.

Beyond ndiswrapper, you might continue to look for how other people installed the prism driver on linux by searching with Google, looking through [http://wiki.ubuntu.com/](http://wiki.ubuntu.com/), etc. Remember, if you decide to start a new thread (which you may want to consider doing, to get some new faces interested in your problem) be sure to describe as accurately and as descriptively as possible the steps you have already taken and the problems you are still having, as well as any relevant output from terminal commands that are you giving you problems. Let me know if there is anything else I can help you with.

---

### Post by KCPokes on 2008-02-11
If it has a key combination to turn wireless on/off, it is typically displayed as a FUNCTION key combination on the keyboard.  For example, on my Gateway it specifically shows wireless is FUNCTION F2.  If there is no key combination, it will not be shown.  Not all have the capability, although anything newer should.

That said, yelling at people trying to help is not going to get a bunch of others to jump in to assist.  Everyone here donates their time to try to help others.  

Back to ndiswrapper.  You loaded the driver.  Now what do you get when you type ndiswrapper -l?  Does it show the driver loaded and, more importantly, working?  I've loaded drivers before only to have it tell me, using the -l flag, that the driver was not loaded correctly, usually due to a version issue.  Have you ensured that you loaded ndiswrapper with modprobe?  Added ndiswrapper to your /etc/modules?  A lsmod will show you if it is loaded and what it is associated with.

---

