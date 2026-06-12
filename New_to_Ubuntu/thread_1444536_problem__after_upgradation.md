---
title: "problem  after upgradation"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by karan_sharma01 on 2010-04-01
i am using ubuntu 8.04 hardy and upgraded it to 8.10.Every thing went smoothly.After booting up with kernel option 2.6.27-17, when i entered the user name and password nothing happened and after some time the screen asking user name and password came again and after entering it the screen came up again.This screen is coming up again and again .
Then i boot up with kernel 2.6.24-27 and 2.6.24.17 and same thing is happening, the screen asking for user name and password is coming again and again .

please help!!!:confused:

---

### Post by Chesamo on 2010-04-01
Support for 8.x ends rather shortly. Any particular reason you're using such an old version?

---

### Post by sandyd on 2010-04-01
> **Chesamo said:**
> Support for 8.x ends rather shortly. Any particular reason you're using such an old version?
he/she is upgrading it step by step.
It is highly unsafe to upgrade from 8.04 directly to 10.04

---

### Post by QIII on 2010-04-01
8.04 is an LTS (Long Term Support).  LTS security support lasts 3 years,  so you reach EOL (End of Life) in April, 2011

8.10 is not an LTS, which means it gets 18 months of support.  It will  reach its EOL this October.  (Wait.  Count on fingers: This April, which it is!)

As for an older version, his hardware (which we do not know about) may be limited by such factors as legacy video drivers (ATI and nVidia both have recently added a lot of cards to their "legacy" lists)

For the OP:

Can you give us some technical specifications on your machine?

Have you tried downloading and burning a LiveCD for 9.10 (Karmic Koala) and seeing how that performs in a Live session?

If you have no hardware issues, you would be much better served upgrading (correct, Carlee) by steps to Karmic (most of the problems have been ironed out) in terms of the length of time until it reaches EOL.  Then again, Karmic caused some people a lot of trouble.

Carlee:  I hope that is what he is doing!

---

### Post by Chesamo on 2010-04-01
My main question is: why upgrade? Building a clean system for scratch is rather satisfying, and if you back up your /home directory (incl. hidden folders) then you don't even have to worry about data loss or redoing settings.

Granted, you *do* have to re-install your programs, but in my opinion that's a low-priority thing.

---

### Post by karan_sharma01 on 2010-04-01
No perticular reason ......i used [https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades) for upgradation ...just that i was  comfortable with 8.04 and didn't think i need the upgradation then .....
can you help me out with the problem???

---

### Post by halitech on 2010-04-01
when you get to the log in screen, hit CTRL + ALT + F1 and see if you can log into the terminal. If it works then I'm guessing its something went screwy with video drivers and its restarting X on you. If it doesn't, maybe it will give us more info on why its not logging you in.

---

### Post by QIII on 2010-04-01
Are you comfortable with the CLI?

---

### Post by sandyd on 2010-04-01
> **karan_sharma01 said:**
> No perticular reason ......i used [https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades) for upgradation ...just that i was  comfortable with 8.04 and didn't think i need the upgradation then .....
can you help me out with the problem???
just to make sure - before I post commands.

Are you using gnome or kde?

---

### Post by karan_sharma01 on 2010-04-01
yups i can log into the terminal with alt+ctrl+f1 .....and i can work in CLI but iam not an expert

---

### Post by QIII on 2010-04-01
Carlee and halitech are both fonts of expertise, so I will leave you in their hands.  I have to go.

But I will leave with this:  Make sure you back up at least your /home partition!

---

### Post by sandyd on 2010-04-01
> **karan_sharma01 said:**
> yups i can log into the terminal with alt+ctrl+f1 .....and i can work in CLI but iam not an expert
then its a problem with gnome/kde

if you can tell us which one your using, we can just give you the instructions to reset the settings, and everything should be fine.

firstly, your using jaunty, so....
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo mv /etc/X11/xorg.conf.original-0 /etc/X11/xorg.conf

```if that complains about a missing file, try
```

sudo mv /etc/X11/xorg.conf.original /etc/X11/xorg.conf
```try logging in again. if it works, YAY!
if not... well... its time to reset the gnome/kde settings....

p.s. 
also try running
```

sudo apt-get update
sudo apt-get upgrade
sudo dpkg --configure -a
```occasionally sometimes the "upgrade" gets partly installed, and the commands above will continue the upgrade if it has halted or been suspended in any way. (which occasionally does happen)

---

### Post by halitech on 2010-04-01
in addition to what carlee has posted, what kind of video card do you have? (general system specs would be nice as well)

---

### Post by karan_sharma01 on 2010-04-01
root@Rocky:/home/karan# lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:02.0 Modem: PCTel Inc HSP56 MicroModem (rev 03)

---

### Post by halitech on 2010-04-01
you may want to look here to see if this helps

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by karan_sharma01 on 2010-04-01
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo mv /etc/X11/xorg.conf.original-0 /etc/X11/xorg.conf

sudo mv /etc/X11/xorg.conf.original /etc/X11/xorg.conf

all these commands complains about a missing file

then i executed 
sudo apt-get update
sudo apt-get upgrade

and then on running dpkg --configure -a 
some processing took place and after some time screen got blanked out ...then i restarted ....and it worked this time ..i logged in gnome but a message appeared in the bottem right corner about "gnome is not ....something ......contact your administator"...
then i ran dpkg --configure -a from terminal in gnome and this time it got executed complitely. but still there is no sound and some problem with network connections .....so i guess the upgradation is still not fully complete ....

---

### Post by karan_sharma01 on 2010-04-01
thanx Carlee and halitech i am glad that now i am able to log in ........but still there is some problem .....like no sound,and mozilla is crashing ubruptly .....is there any way to make it work fully 100 percent....???

---

### Post by sandyd on 2010-04-01
BRB. encountered some police tape while driving home so gotta take a detour... (traffic isnt moving at all....)

---

