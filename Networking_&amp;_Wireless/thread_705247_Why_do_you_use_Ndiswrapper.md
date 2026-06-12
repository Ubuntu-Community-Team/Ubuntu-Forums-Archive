---
title: "Why do you use Ndiswrapper"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by KOTAPAKA on 2008-02-23
I remember how happy i was when I first installed Ubuntu and I remember the sorrow when I couldn't set up my wireless card. I remember reading quite a lot of stuff about using ndiswrapper and doing things and using commands which at that time were like quantum mechanics for me. I never found though the simple explanation of setting the wireless (especially Broadcom 43xx as these are quite popular and at the same time have no support for Linux) with fwcutter in just 2 steps:
1. Install fwcutter (offline)
2. Put the firmware (offline)

And what is most important for new users - can be done via the GUI.

---

### Post by kevdog on 2008-02-23
With linksys cards for the Gutsy kernel, in most cases ndiswrapper offers a more stable, reliable connection, with better range, and a max bandwidth of 54 mb/sec compared to 11 mb/sec.  As far as quantam mechanics -- if you can't read about 10 instruction steps for installation of ndiswraper, then you are going to have problems tying your shoes!

---

### Post by luisromangz on 2008-02-23
I do use ndiswrapper becuase bcm43xx drivers doesn't provide a reliable connection for me, and ndiswrapper does. Also, there are GUIs for ndiswrapper, although they are not installed by default in Ubuntu.

Besides, ndiswrapper is really easy to setup, once you now what driver you have to install, it involves only a few commands in a terminal, en less than 5 minutes you can have you wireless card working.

---

### Post by mrsteveman1 on 2008-02-23
Broadcom actually did develop a driver for their BCM943XX chips, they just never released it to the public. Linksys routers use the binary version of this driver (compiled against one version of the 2.4.x series kernel). They actually have less excuse than a lot of companies for not supporting linux, they already spent the time to develop a driver and still don't release it.

Firmware is also annoying, lots of companies have granted linux distributions the right to distribute their firmware with the system, if you check the ubuntu gutsy livecd you will find quite a few different wireless firmware files for random wireless cards in /lib/firmware/. Broadcom could do this and hasn't.

There is hope though, the new b43 driver in 2.6.24 seems quite stable to me and works well all the way to 54Mbps on my laptop.

---

### Post by kevdog on 2008-02-23
Broadcom -- so much potential, such a waste of time.  Hopefully the b43 driver will be useful -- if only however the chipset maker would release the driver and not a third party.

---

### Post by mrsteveman1 on 2008-02-23
I used to think broadcom made nice chips but now im not sure, broadcoms own driver on windows drops connections randomly on many laptops.

I also know the newer macs use a broadcom 4328 chip, and they seem to be having serious problems as well, dropping connections randomly etc.

---

### Post by KOTAPAKA on 2008-02-23
> **mrsteveman1 said:**
> Broadcom actually did develop a driver for their BCM943XX chips, they just never released it to the public. Linksys routers use the binary version of this driver (compiled against one version of the 2.4.x series kernel). They actually have less excuse than a lot of companies for not supporting linux, they already spent the time to develop a driver and still don't release it.

Firmware is also annoying, lots of companies have granted linux distributions the right to distribute their firmware with the system, if you check the ubuntu gutsy livecd you will find quite a few different wireless firmware files for random wireless cards in /lib/firmware/. Broadcom could do this and hasn't.

There is hope though, the new b43 driver in 2.6.24 seems quite stable to me and works well all the way to 54Mbps on my laptop.

Does this mean that if I upgrade my kernel to 2.6.24 I will get a better connection?

---

### Post by KOTAPAKA on 2008-02-23
true sometimes native drivers nag while opening a page.

---

### Post by mrsteveman1 on 2008-02-23
With respect to 2.6.24, yes the b43 driver is massively better than bcm43xx. In particular it uses the 4.x series firmware for the chips, the old bcm43xx driver only used the 3.x series firmware. 

If you really want to you can grab the mainline source and compile it (its not that hard really, max 6 commands). You will also have to get the new firmware for the driver and the new firmware extractor [here]("http://linuxwireless.org/en/users/Drivers/b43").

On windows, the problem seems to be that the driver literally drops the connection to the access point, you can tell because everything stops working just like if you had turned the card off.

---

### Post by mrsteveman1 on 2008-02-23
Found something interesting, the linuxwireless people seem to have backported the newest drivers for use with the 2.6.22 kernel, which coincidentally is used in ubuntu gutsy.

I haven't tried this yet but they provide a package and instructions [here]("http://linuxwireless.org/en/users/Download") for installing the new drivers into the older kernel so you don't have to upgrade the entire kernel to use them.

---

### Post by dje on 2008-02-23
ndiswrapper allows my Broadcom 1390 (Dell Wireless 1390) card to operate at full speed :)

dje

---

### Post by KOTAPAKA on 2008-02-23
yep I know this site but I am using debian and so it doesn't work for me (2.6.18 :() I will try it in my ubuntu.

---

