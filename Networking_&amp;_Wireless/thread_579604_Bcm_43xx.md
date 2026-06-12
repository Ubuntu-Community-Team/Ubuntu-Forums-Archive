---
title: "Bcm 43xx"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by tiki28 on 2007-10-18
I thought that BCM4306 was supposed to work out of the box with 7.10. It does with the SimplyMepis Beta.

I would like it to work with Ubuntu, am I doing some thing wrong?

Help?

---

### Post by android6011 on 2007-10-18
did you install the restricted driver?

---

### Post by CeeDub on 2007-10-18
I am a little dissappointed it doesn't work straight off the Live CD.  I even tried to enable the restricted driver, but it won't work.  Maybe I have to have an active internet connection to download fwcutter?

---

### Post by potentia on 2007-10-18
Yes. It killed my drivers, now asking me to be online to get the driver. DUUUH!
 
Further, now my ethernet cable doesn't work either. Always did in any basic Ubuntu install. I think this is the end of the line for Linux for me. Too much trouble.
 
I have no idea about what I should do now.

---

### Post by KCPokes on 2007-10-18
> **potentia said:**
> Yes. It killed my drivers, now asking me to be online to get the driver. DUUUH!
 
Further, now my ethernet cable doesn't work either. Always did in any basic Ubuntu install. I think this is the end of the line for Linux for me. Too much trouble.
 
I have no idea about what I should do now.

Not that it'll help but even in Windows most wireless cards dont work "out of the box".  At least for me anyway.  I wouldn't attempt to install any OS, using wireless, if I didn't have a wired backup.

As far as Broadcom goes it always seems like a crapshoot as to which ones work and how well they'll work.  I've had mixed luck using the restricted drivers thus I still choose to resort to using ndiswrapper with the Windows 98 drivers for your card.  It is as simple as downloading your drivers to your machine, installing ndiswrapper (and ndiswrapper-utils), and issueing the "ndiswrapper -i <inf file>".   I choose to reboot at this point and check my dmesg for messages related to that device (specifically you are looking to see whether the driver initialized the card or not).  At that point you are now to the point that you need to configure your wireless network, using NetworkManager or WICD.

---

### Post by potentia on 2007-10-18
It is not the driver availability that is the only issue, it is just so damn hard to install and configure it. Made it once, now it doesn't work. 
 
I am currently removing the Ubuntu partition, I can't find the motivation to spend days on struggling with HOW TO's again. I just tried, they didn't help me.
 
EDIT: stubborn as I am I made it work. I installed Gutys again again...

---

### Post by tiki28 on 2007-10-19
I have ubuntu 7.04 working with netwrapper I an afraid to up grade to 7.10

---

### Post by bmartin on 2007-10-19
> **tiki28 said:**
> I have ubuntu 7.04 working with netwrapper I an afraid to up grade to 7.10
I can't blame you. I upgraded and my internet stopped working for several reboots, then mystically started working again, for no apparent reason... nothing seemed to change, other than I kept rebooting... I tried other kernels with the same results, and sometimes my computer gets hung on "loading hardware drivers"... I seem to be having random problems with Gutsy.

Why is it that each time a new version of Ubuntu comes out, the wireless support gets worse? The results of Edgy vs. Feisty have been measurable; there was a long-running thread for installing fresh vs. upgrading, and in both cases, Edgy reigned supreme for WiFi support. I'm thinking that Gutsy will be a regression.

And why aren't the RT drivers from serialmonkey.com included by default? They're pretty stable and released under the GPL. They work quite well with RutilT.

---

### Post by potentia on 2007-10-19
If it works, don't fix it. Gutsy is not a major update, you can safely skip this update. Especially if you got the wireless and what not working in Feisty.

It is not fun upgrading Ubunty. I have to remove tons of fonts and programs every time I reinstall, and usually it breaks everything so I have to reinstall and reconfigure everything.

Skip Gutsy and be productive for another 6 months.

---

