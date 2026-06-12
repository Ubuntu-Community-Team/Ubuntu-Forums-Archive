---
title: "Problem connecting to the internet"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by David Ostrom on 2007-04-23
Hello,
I’m hoping someone can help me connect to the internet. I have Ubuntu 7.04 Feisty with a newly installed U.S. Robotics USR5610B modem. The modem dials up my provider but when I click on the Firefox browser, nothing happens and then it disconnects.
Can someone give me a step by step being I’m new to Ubuntu and Linux.
Thank you in advance,
David Ostrom

---

### Post by mainely_linux on 2007-04-23
I believe you are having the same problem as me.  I haven't had any luck getting a reply on my issue.  If you install 6.10 Edgy your hardware and connection will work.

See my thread:

[http://ubuntuforums.org/showthread.php?t=419825](http://ubuntuforums.org/showthread.php?t=419825)

---

### Post by David Ostrom on 2007-04-23
Hi mainely_linux,
Thanks for the reply.
I checked out your previous post. I had 6.10 installed with a winmodem and did some reading and found out that it was more than I could handle so after doing some research I picked up a U.S. Robotics 5610 modem thinking this would solve all my problems. I installed the modem and I get nothing (no dial-up). I saw Feisty fawn had just been released so I’m thinking; I’ll give it a try. So after install I try to connect to the internet but this time i get dial-up and then it drops. I have no idea where to begin searching or what to look for, I have a couple of books on hand (Ubuntu Linux Bible and Linux Phrasebook for code and commands) but I think they just scratch the surface.

Thank you again, I’ll let you know if I find out anything.
David

---

### Post by Bartender on 2007-04-26
It's a cryin' shame that us dial-up users, who are already in hell, spend money for hardware modems then find the latest version of Ubuntu is worse instead of better.
I wonder if PCLOS or MEPIS might work better?

---

### Post by mainely_linux on 2007-04-26
> **Bartender said:**
> 
I wonder if PCLOS or MEPIS might work better?

Not familiar with those.  

I have a software modem (smartlink) in my laptop, but I choose to use a basic pcmcia 56k modem.  Both work (in 2.6.17-10 kernel), however the slmodem stuff is a bit complicated but not too outrageous.  I was able to find a precompiled binary for slmodemd that worked well in my case.  What winmodem do you have?

---

### Post by jitsu on 2007-04-27
I just upgraded to Ubuntu 6.10 this morning and am unable to get my dial up modem working. It worked in the previous version--

I'm following the instructions in "Ubuntu Linux for Non-Geeks".

I have followed all steps up to the point where the author states to click the autodetect button. He states that it performs  SCAN OF YOUR PORTS AS IT LOOKS FOR A LIVE MODEM.

I don't have an autodetect button that I can find and I feel that's where my problem lies.  Is there a detailed instruction for connecting with a dial up modem for Ubuntu 6.10?

Any help appreciated.

thanks

---

### Post by mainely_linux on 2007-04-27
> **jitsu said:**
> I don't have an autodetect button that I can find and I feel that's where my problem lies.

I suspect the guide is talking about kppp or gnome-dialer, each of which I think has a detect modem feature.  You may try wvdial, and its helper program wvdialconf - which will detect your modem and assign it to the correct serial device.

---

### Post by Bartender on 2007-04-28
jitsu -
Just to confirm, Dapper had the Auto-detect, Edgy dumped it.  I imagine the story's the same with Feisty.  Do you remember where the modem was in Dapper?  I've found ttys0 to be the most likely spot.  That makes sense for an external, but ttys0 was even the location for an internal modem I was dinking around with the other day.  Of course it didn't work :(  but that's where the OS found a modem responding.

---

### Post by kent69 on 2007-04-28
I ahve the same problem with external us robotices sortster the ubuntu doesnt see it at all and dont know how to us the net :( and nobody answered me????

---

### Post by jitsu on 2007-04-28
Bartender:
You were right on, on the location of the modem. I went back to Dapper and had absolutely no problems connecting to the internet. 

Fortunately I have two computers Windows XP and Ubuntu--and was able to access the forum. 

With me it's essential that I have the ability to access the internet. My Zip Drive, External DVD writer all work without a problem. I need a printer driver and that will put me in good shape.

I'm still learning at an advaced age.


thanks

---

### Post by Michl on 2007-05-03
Well, misery loves company. 

Dialup has deteriorated in Ubuntu.

Dapper:  wvdial and Admin -> Network are functional

Edgy:  wvdial is functional,  (not Admin -> Network)

Feisty:  neither work.

What is funny is they tried to fix it so that now you
can configure and dial in Network, but it keeps disconnecting
and in the process they screwed-up wvdial and ppp.

You can use the modem in edgy.  But you need to use
wvdial and gnome-ppp makes this easy.

M

---

### Post by Michl on 2007-05-04
Just discovered something odd.  In edgyu the modem is
on ttyS2, in dapper it is on S4.  As a result admin ->network
can;t get to it because it only goes up to s3

---

### Post by Bartender on 2007-05-04
Michl -
I haven't bothered to try my external Sportster with Feisty.  You're saying Feisty is worse than Edgy?  Even wvdial doesn't work??
Is this something you tried first-hand or heard it to be true?

The whole K/X/Ubuntu effort has been a great thing for Linux in general but apparently they view dial-up users as disposable.

---

### Post by mainely_linux on 2007-05-04
The only way for me to get dialup working in Feisty is to go back to 2.6.17-10-generic.  The default Feisty kernel causes it to drop on internet traffic.

---

### Post by Michl on 2007-05-04
> **mainely_linux said:**
> The only way for me to get dialup working in Feisty is to go back to 2.6.17-10-generic.  The default Feisty kernel causes it to drop on internet traffic.

I am curious about this.  SO you can install Feisty, but then download the Edgy kernel
and still run Feisty?

Michael

---

### Post by mainely_linux on 2007-05-04
> **Michl said:**
> I am curious about this.  SO you can install Feisty, but then download the Edgy kernel
and still run Feisty?

Michael

Yes, it works fine.  I have 3 different kernels installed in fact.  The Feisty kernel is what I boot when I'm at work as I use wireless there and it functions fine.

When I'm at home in the boonies, I boot the 2.6.17-10 kernel from edgy (by choosing it as an option in grub upon boot) so I can utilize my modem.

---

### Post by Michl on 2007-05-04
> **Bartender said:**
> Michl -
I haven't bothered to try my external Sportster with Feisty.  You're saying Feisty is worse than Edgy?  Even wvdial doesn't work??
Is this something you tried first-hand or heard it to be true?

The whole K/X/Ubuntu effort has been a great thing for Linux in general but apparently they view dial-up users as disposable.

First-hand.  First I configured the modem in Admin _> network and it connects in the final version of
Feisty, but I kept getting disconnected anytime I tried to do anything, e.g. open a webpage, download packages, and so on.  I expected this because I think I read this on the launchpad, so then I tried to do it the Edgy way by configuring wvdial.  I spent 2 hours messing with various init2 entries, from the basic to the complex.  In any case what worked in Edgy did not work in Feisty anymore.  So checked this forum to confirm that others have had this problem.  Just to double check, I dialed in from another computer running edgy with no problem.  Then I decided to install Dapper on the one where I had Feisty, and had no problems with wvdial.  In fact, was downloading upgrades to dapper all night long without one disconnect.

M

---

### Post by Michl on 2007-05-04
> **mainely_linux said:**
> Yes, it works fine.  I have 3 different kernels installed in fact.  The Feisty kernel is what I boot when I'm at work as I use wireless there and it functions fine.

When I'm at home in the boonies, I boot the 2.6.17-10 kernel from edgy (by choosing it as an option in grub upon boot) so I can utilize my modem.

Since I did a clean install, I don;'t get that choice in Grub.  So I looked in synaptic for that linux image, but I cannot find it there.  Once you are in Feisty, where do you find it?

Maybe you upgraded from edgy and the upgrade leaves the old kernel, but if you do a clean install the old kernel vanishes?  Just speculating./

M

---

### Post by mainely_linux on 2007-05-04
> **Michl said:**
> Since I did a clean install, I don;'t get that choice in Grub.  So I looked in synaptic for that linux image, but I cannot find it there.  Once you are in Feisty, where do you find it?

Maybe you upgraded from edgy and the upgrade leaves the old kernel, but if you do a clean install the old kernel vanishes?  Just speculating./

M

I did upgrade from edgy.  But you can just go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and search for the kernel images/headers/modules, download and install them - it will add the grub choices for you (at least it should)

---

### Post by mainely_linux on 2007-05-04
> **mainely_linux said:**
> I did upgrade from edgy.  But you can just go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and search for the kernel images/headers/modules, download and install them - it will add the grub choices for you (at least it should)

Specifically I used these:

[http://packages.ubuntu.com/edgy/devel/linux-headers-2.6.17-10-generic](http://packages.ubuntu.com/edgy/devel/linux-headers-2.6.17-10-generic)
[http://packages.ubuntu.com/edgy/base/linux-image-2.6.17-10-generic](http://packages.ubuntu.com/edgy/base/linux-image-2.6.17-10-generic)
[http://packages.ubuntu.com/edgy/misc/linux-restricted-modules-2.6.17-10-generic](http://packages.ubuntu.com/edgy/misc/linux-restricted-modules-2.6.17-10-generic)

---

### Post by Michl on 2007-05-04
Hmmm I think this basically means you are booting into Edgy.  When you are booting
into that kernel you are not in Feisty but in edgy.  Does that seem right?

---

### Post by mainely_linux on 2007-05-04
Nah the software is all Feisty, and the login screen says feisty as well.  It's just that I'm running a different kernel under feisty than what comes with it by default (at least when I'm at home wanting to actually use my modem)

---

