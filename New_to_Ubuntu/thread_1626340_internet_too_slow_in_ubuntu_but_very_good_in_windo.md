---
title: "internet too slow in ubuntu but very good in windows"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by magedsoft on 2010-11-20
hay all : 

i install windows 7 and ubuntu 10.10 at windows my speed is 128kb/s
but at ubuntu 30 or 50 kb/s 


what's the problem

---

### Post by Gone fishing on 2010-11-20
Need more information

How do you connect to the net?
What hardware are you using?

---

### Post by magedsoft on 2010-11-20
my internet dsl 
my hardware etheros lan

---

### Post by asmoore82 on 2010-11-20
Where are you getting these speed measurements from?
IMHO, those "test your connection speed" sites are no good.

Try downloading a huge file like an Ubuntu .iso for a better test of speed.

---

### Post by dnyal on 2010-11-20
I'm having this same issue. Everything was just fine with 10.04. Now I'm using 10.10 (fresh install), and my internet connection, despite being stable, is pretty slow. It takes to Firefox and Opera like a century to load any site. Sometimes it loads the webpage almost completely, but any of those 2 browsers then hangs up at 99% and continues to load the site indefinitely. My wireless doesn't work at all. 
I have a Dell inspiron 1464 with a broadcom wireless device. Thanks for any help.

---

### Post by mihaiflorentin88 on 2010-11-21
i`ve been having a similar issue with ubuntu 10.10. Are you using torrent applications ? I`m asking because i noticed some kind a conflict with my torrent applications. I mean the internet works just fine until i start a torrent client,then,no matter if i close the torrent application or not,the internet will run quite slow until i reboot the system. Does anyone know a fix for this ?

---

### Post by wojox on 2010-11-21
> **mihaiflorentin88 said:**
> i`ve been having a similar issue with ubuntu 10.10. Are you using torrent applications ? I`m asking because i noticed some kind a conflict with my torrent applications. I mean the internet works just fine until i start a torrent client,then,no matter if i close the torrent application or not,the internet will run quite slow until i reboot the system. Does anyone know a fix for this ?

You need to configure your torrent. [BitTorrent optimization and troubleshooting guide]("http://art.ubuntuforums.org/showthread.php?t=1259923")

---

### Post by wojox on 2010-11-21
> **magedsoft said:**
> hay all : 

i install windows 7 and ubuntu 10.10 at windows my speed is 128kb/s
but at ubuntu 30 or 50 kb/s 


what's the problem

Are you using Wubi?

---

### Post by pabelmont on 2011-01-13
I have the same problem. Using 10.04 (Lucid Lynx) and WindowsXP on one PC. 

Internet speed is quite good on windows (as it used to be on Ubuntu), just awful (FireFox, Opera) on Ubuntu. 

The time is not so much in identifying the remote server (DNS?) but in transmitting pages, and the VERY WORST is trying to re-transmit a FORM using "F5" as a "hurry-up". Usually, after "F5" on FireFox, I just get a time-out. Opera doesn't seem to "time-out" but takes just as long -- little blue box on URL shows slowly up-creeping numbers (56:76) --> (75:76) --> (76:83) etc.

To get any web-based work done I'm more and more using Windows, which I regret. I mean, why did I get Ubuntu in the first place?

I really don't understand "configuration" and may well have done something to slow-down my machine. But I have no idea what.  What could I re-install, or what testing could I perform, to identify the problem?

---

### Post by TenPlus1 on 2011-01-13
Strange, my Ubuntu internet is much faster than Windows...  You could try disabling IPV6:

In terminal type   sudo gedit /etc/default/grub   and change:

GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”

to

GRUB_CMDLINE_LINUX_DEFAULT=”ipv6.disable=1 quiet splash”

then type   sudo update-grub

also the firefox tweaks page may help improve performance:

[http://www.tweakguides.com/Firefox_1.html](http://www.tweakguides.com/Firefox_1.html)

---

### Post by jonpon on 2011-01-13
> **magedsoft said:**
> hay all : 

i install windows 7 and ubuntu 10.10 at windows my speed is 128kb/s
but at ubuntu 30 or 50 kb/s 


what's the problem

Does it actually take longer to download something or are you just going off the stats?  Windows (as far as I'm aware measures in Kib/s that's (kiloBITS not kiloBITES) Whilst my Ubuntu give me the speed in KiB/s that's BITES

The difference is in the letter-case.
 bits have a lower-case "b" hence Kib or Kb
 whilst Bites have an Upper-case "B" hence KiB or KB

I download at a speed of around 2000Kib/s according to my router 
    UBUNTU measures it at around 250KiB/s
8 bit= 1 Bite

---

