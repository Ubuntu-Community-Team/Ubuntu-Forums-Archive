---
title: "I'm getting a Wacom Bamboo Pen and Touch tablet in a few days."
date: 2011-02-01
forum: New to Ubuntu
---

### Post by MatthewWilliams on 2011-02-01
Hi, I've seen the tutorial on how to get Bamboo tablets working with Ubuntu. However, it's big, scary and has lots of words. Is there a tutorial anywhere on how to do it that I could understand?

Thanks.

**EDIT:** I did a bit more google searching and found this. Can someone confirm that it works?

```
sudo add-apt-repository ppa:doctormo/wacom-plus
sudo apt-get update
sudo apt-get install wacom-dkms
```

---

### Post by Favux on 2011-02-01
Hi Matthew,

It'll depend on your tablet model.  The usb kernel driver wacom.ko used is dated and may not have your model if it is new enough.  In which case the dkms setup will interfere with you getting your tablet working.

Just skim the HOW TO so you know where things are.  If the tablet is one of the 5 origninal ones and you are in Maverick all you need is part I. to get it working.

---

### Post by MatthewWilliams on 2011-02-01
> **Favux said:**
> Hi Matthew,

It'll depend on your tablet model.  The usb kernel driver wacom.ko used is dated and may not have your model if it is new enough.  In which case the dkms setup will interfere with you getting your tablet working.

Just skim the HOW TO so you know where things are.  If the tablet is one of the 5 origninal ones and you are in Maverick all you need is part I. to get it working.


I'm in Maverick (that's 10.10, right?) and it's new. -_-


I guess I will look through the HOW TO again and pretend to comprehend it.

**EDIT:** I meant "attempt", but pretend works just as well. :P

---

### Post by gun0 on 2011-02-02
Hello, yesterday I tried to install Wacom Bamboo Fun Pen & Touch. I  gave up so far. In total it took me 5 h to install the "Ubuntu Studio".  First the downloaded image from the top link of the Studio site  ("altrernate setup") was corrupted (correct md5sum missing in the  gsfonts), luckily the links below were o.k. (2h)

Another three hours with the tablet. The Wikis are really cryptic. For  Maverick two scripts were offered, but without registration  not  acessable.

But finally I could understand the procedure.
1. you will need a kernel patch and create the module for the newer  tablets. (So far I don´ t know if you have to recompile the kernel, or  the module only or it is precompiled ... 

2. you will have to define this input device in the configuration file  of the X-Window system, same as for keyboard, mouse and monitor. 

3. there are several possibilities to do that. One I believe are the  scripts which will be put into the init file for the runlevel where X is  started. 

In my opinion the easiest would be to get a copy of the device  declaration in xorg.conf and best a precompiled kernel-image for the  newer wacom tablets. I was very surprised not to find an adapted kernel.  in the "Studio Edition" but the ubuntu generic.

Anyway, my son wants to work with his tablet making drawings and is not  very interested in computer administration. So we gave up.
Maybe I will try again to find a solution. If successful I will post the kernel image and config files.
But at this moment I am too frustrated. Really, it was easier to get X  running with SuSE 5.1 (1997) than this tablet today. Anyway many thanks  to the community who made this "Studio Edition" avaliable. Unfortunately  I am too stupid and too impatient to spend hours configuring and after  an distupgrade all is broken? This is what the wikis also indicate.

---

### Post by Favux on 2011-02-02
Hi gun0,

Welcome to Ubuntu forums!

The model is on the back of the tablet and we can get product ID by entering in a terminal:
```
lsusb
```
Unfortunately you loaded "Ubuntu Studio".  That's the flavor we have the most problems with installing a Bamboo P&T.  Out of curiosity can I ask why you wanted "Ubuntu Studio"?

It also helps to know which release it's based on, Maverick, Lucid, etc.  If you don't know we can look at the kernel and X server versions.  Enter in a terminal:
```
uname -r
```
```
Xorg -version
```
> In Maverik two scripts were offered, but without registration not acessable. 
What?
> The Wikis I found were not really understanbable.
Which ones and why?

---

### Post by gun0 on 2011-02-02
Thank you for your reply. We did choose Ubuntu Studio-latest edition, because my son is drawing comic strips and I wanted to show him that with a linux box he has additional features, though he prefers Photoshop on Windows XP. He knows Gimp tested under OsX and SuSE 10.

Myself I always had since SuSe 5.1 a linux box for banking etc. Of course I tried Ubuntu. I think it is great. Many thanks to the community. It is easy to install and reliable. A good desktop enviornement for everyone.

---

### Post by Favux on 2011-02-02
If you follow the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") it should only take and hour or so to get everything working.  Depending on how much you wanted to do.  Even though you have to take into account you have a new model.

The caveat is Studio.  It seems like people run into problems with that flavor of Ubuntu and the problem seems different each time.  At least I haven't noticed a pattern yet.  So you might be better off installing Ubuntu Maverick first and going from there.

---

### Post by gun0 on 2011-02-02
Sorry I did not answer your questions properly. At first I tried:

leon@bertel:~$ uname -r
2.6.35-25-generic

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
Current Operating System: Linux bertel 2.6.35-25-generic

leon@bertel:~$ lsmod no entry for wacom 

leon@bertel:~$ modprobe -l | grep wacom*
kernel/drivers/input/tablet/wacom.ko
kernel/drivers/input/touchscreen/wacom_w8001.ko
kernel/drivers/hid/hid-wacom.ko

leon@bertel:~$ lsusb
Bus 002 Device 002: ID 056a:00d8 Wacom Co., Ltd 

So this I checked after installation, because the tablet did not work.

Then I tried modprobe wacom.co, lsmod o.k., but dmesg, messages no registration.

The wiki` s are cryptic: [http://ubuntuforums.org/showpost.php?p=8262965&postcount=54116881](http://ubuntuforums.org/showpost.php?p=8262965&postcount=54116881)

# wget [http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h](http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h)
# cp ./hid-ids.h /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h
# apt-get install patch

# tar -xjvf linuxwacom-0.8.4-3.tar.bz2
# tar -xjvf wcm2_patch.tar.bz2        
# cp wcm2_patch/*.patch linuxwacom-0.8.4-3/     
# cd linuxwacom-0.8.4-3/

Which is the working directory? home?root? /usr/src?

[http://ubuntuforums.org/showthread.php?p=9496609#post9496609](http://ubuntuforums.org/showthread.php?p=9496609#post9496609)
**[SIZE=3][COLOR=SeaGreen]Sample xsetwacom scripts for other tablets and tablet pc's attached to post #2 below.[/COLOR][/SIZE]**

**Wacom Bamboo Pen & Touch models and supported devices**

This is the headline followed by a box "code".

Two lines below that box you have "Pad Buttons (see [screen shot]("http://ubuntuforums.org/showpost.php?p=8608357&postcount=784")):" Without registration, no screenshot. So now I am registered and the links not only the one above are working. 

It is cryptic because without knowing what to do, not understanding the principle, I do not know what this wiki wants to tell me. Finally I found out: usb-driver and x-setup.
Then the form of presentation, scroll, scroll scroll ... 

I believe two sentences below the headline would make the post comprehensive. e.g. for installation of the wacom hardware you need 1st the usb driver 2nd...You proceed like this and this. Then the details may follow.

Now, after understanding the principles I can read this wiki different. And I understand that once you are familiar with these tabelt installations it is maybe too comprehensive, but staring from zero it is too difficult. 

Anyway, thank you for your support and your interest in my computer problems. And  thanks to the comunity. I feel a little bad. There are many volunteers providing programs and support and I complain...

Finally reporting about my bamboo problem made me understand more and I believe I can get it working properly.

---

### Post by Favux on 2011-02-02
OK, you have the Maverick kernel and X server so your Studio is a flavor of Maverick.

kgingeri's little how to is very dated and is from when we were developing the Bamboo P&T drivers.  You do want the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

Right, to get your very new Bamboo working you need a very recent X driver, i.e. clone the xf86-input-wacom git repository.  Because all of the new Bamboo models are in it as of 12 days ago.

And of course you need a usb kernel driver (wacom.ko) that has your model in it.  You either add it manually to the wacom_wac.c source code of linuxwacom 0.8.8-10 or install the new input-wacom 0.10-1 as described in post #2.  And then for linuxwacom you'd complete part I.

If you want to see comprehensive go to the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1"), which you would do to install input-wacom (the alternate section 1).

You'll see the Bamboo HOW TO is actually very pared down and lean.  I get complaints either way.  To comprehensive or I don't explain what's going on.  What can you do?

---

