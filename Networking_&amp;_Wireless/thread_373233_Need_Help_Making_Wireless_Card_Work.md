---
title: "Need Help Making Wireless Card Work"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by adarkmethod on 2007-03-01
My laptop has an Intel Pro 2915abg built in wireless card. Does anyone know how I can make it work with Ubuntu edgy Eft? Im having to use the XP boot until i can get that working and i'd much much rather go back to Ubuntu


I should also probably note that im new to Linux, I installed Ubuntu earlier tonight, and i dont know anything about using command line, sorry if that makes me harder to help

---

### Post by mac.ryan on 2007-03-01
I am not a superexpert in Ubuntu either, but in my case, it was rather easy:
[LIST=1]
[*]System --> Administration --> Networking
[*]Activate "wireless connection" (right click or one of the tab, I don't remember)
[*]Configure SIID, password, etc...[/LIST]Off you go!

PS: what I did to know what WiFi are available in one place, was to install (from Synaptics package manager) "WiFi radar". I suppose you can use that also to configure WiFi directly, but I didn't do it, so I don't know if it works esily or not...

Best luck!

---

### Post by adarkmethod on 2007-03-01
Actually Ubuntu isnt eve recognizing the card tho, thats the problem, it wont even search for a signal. thanx tho

---

### Post by mac.ryan on 2007-03-01
> **adarkmethod said:**
> Actually Ubuntu isnt eve recognizing the card tho, thats the problem, it wont even search for a signal. thanx tho

I am not a linux expert, so I fear I can't help further, the only things I can think of is that your card is off although you believe is on (on my previous laptop the led of the WiFi card got weird, under ubuntu.

Also: do you see the device in the device manager? Is there any info there that can help understanding what the problem is?

---

### Post by adarkmethod on 2007-03-01
I was actually able to find a driver on the Intel site that is for Linux, i dont however have ANY clue how to install the driver, tho i do have it downloaded

---

### Post by chili555 on 2007-03-01
I assume you have a tar.gz file? Here are instructions for building from sourcecode, i.e. tar.gz files: [http://www.thinkwiki.org/wiki/Ipw2200](http://www.thinkwiki.org/wiki/Ipw2200)

As for the ieee80211 stack, I'd think you'd be better off getting the Ubuntu package: apt-get install ieee80211-source. It will want you to take some dependencies, which you should.

As always, in Ubuntu, precede every command with sudo. Your card should then be recognized and configurable.

Post back if you get stuck.

---

### Post by adarkmethod on 2007-03-01
> **chili555 said:**
> I assume you have a tar.gz file? Here are instructions for building from sourcecode, i.e. tar.gz files: [http://www.thinkwiki.org/wiki/Ipw2200](http://www.thinkwiki.org/wiki/Ipw2200)

As for the ieee80211 stack, I'd think you'd be better off getting the Ubuntu package: apt-get install ieee80211-source. It will want you to take some dependencies, which you should.

As always, in Ubuntu, precede every command with sudo. Your card should then be recognized and configurable.

Post back if you get stuck.


Ok, i'll check those out, I do need to state tho that I have never used the Linux/Ubuntu Command Line Interface before, so this is all a little overwhelming for me

---

### Post by adarkmethod on 2007-03-01
Ok, i got the ieee80211 source installed using apt-get, but none of the stuff on that wiki is working for me, Im sure its jsut me typing something wrong, is there any ways someone could get on one of the messengers(MSN, yahoo, AIM) and walk me through it? I'd really appreciate it.

---

### Post by adarkmethod on 2007-03-01
i've put both of those TZG files on my desktop, here's what it looked like when i tried to install through terminal



adarkmethod@adarkmethod:~$ sudo apt-get install ieee80211-source
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  debhelper dpkg-dev html2text module-assistant
Suggested packages:
  dh-make debian-keyring fakeroot build-essential
The following NEW packages will be installed:
  debhelper dpkg-dev html2text ieee80211-source module-assistant
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 864kB of archives.
After unpacking 2687kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) edgy/main dpkg-dev 1.13.22ubuntu7 [110kB]
Get:2 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) edgy/main html2text 1.3.2a-3 [95.5kB]
Get:3 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) edgy/main debhelper 5.0.37.3ubuntu4 [508kB]
Get:4 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) edgy/universe module-assistant 0.10.6 [80.5kB]
Get:5 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) edgy/universe ieee80211-source 1.1.6-4 [70.6kB]
Fetched 864kB in 6s (138kB/s)                                                  
Selecting previously deselected package dpkg-dev.
(Reading database ... 114906 files and directories currently installed.)
Unpacking dpkg-dev (from .../dpkg-dev_1.13.22ubuntu7_all.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3_i386.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_5.0.37.3ubuntu4_all.deb) ...
Selecting previously deselected package module-assistant.
Unpacking module-assistant (from .../module-assistant_0.10.6_all.deb) ...
Selecting previously deselected package ieee80211-source.
Unpacking ieee80211-source (from .../ieee80211-source_1.1.6-4_all.deb) ...
Setting up dpkg-dev (1.13.22ubuntu7) ...
Setting up html2text (1.3.2a-3) ...

Setting up debhelper (5.0.37.3ubuntu4) ...
Setting up module-assistant (0.10.6) ...
Setting up ieee80211-source (1.1.6-4) ...
adarkmethod@adarkmethod:~$ sudo apt-get install ipw2200-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ipw2200-source
adarkmethod@adarkmethod:~$ # tar xzvf ipw2200-1.2.0.tgz
adarkmethod@adarkmethod:~$ #cd ipw2200-1.2.0
adarkmethod@adarkmethod:~$ #make
adarkmethod@adarkmethod:~$ #make install
adarkmethod@adarkmethod:~$ apt-get install ipw2200-source
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
adarkmethod@adarkmethod:~$ tar xzvf ipw2200-1.2.0.tgz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
adarkmethod@adarkmethod:~$ tar xzvf ipw2200-1.2.0.tgz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
adarkmethod@adarkmethod:~$ tar xzvf ipw2200-fw-3.0.tgz -C /lib/firmware
tar: ipw2200-fw-3.0.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
adarkmethod@adarkmethod:~$

---

### Post by ehorgan on 2007-03-05
I have been having similar problems.  I have been trying this now for weeks, and have been dual booting between Windows and Ubuntu 6.10 when I need to get on wireless (I have no problems with wireless in Windows).

I have tried every tutorial under the sun.  

I have clean re-installed Ubuntu onto it's partition and tried over, nothing seems to work.

Ideas?

---

### Post by adarkmethod on 2007-03-05
I've found that if i install Kwlan it will work. My wireless LED still doesnt light up, but its on and i have a signal.

---

### Post by mac.ryan on 2007-03-05
Excellent! I am happy for you! :)

---

### Post by adarkmethod on 2007-03-05
me too, too bad i didt figure it out til i got back home where i have an ethernet cable tho

---

