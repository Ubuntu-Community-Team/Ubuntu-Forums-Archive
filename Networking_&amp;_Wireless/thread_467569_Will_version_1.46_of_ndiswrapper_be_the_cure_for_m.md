---
title: "Will version 1.46 of ndiswrapper be the cure for my bcm4318?"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by plinydogg on 2007-06-07
It doesn't matter what I do. I can't get my Broadcom bcm4318 to work no matter what. I've tried using fwcutter with bcm4318 and I've tried ndiswrapper with my Windows drivers. Nothing works. 

I read a few threads where people said that the only way they got their card working was to download the latest version of ndiswrapper (version 1.42, 1.45, or 1.46) and compiling it and then using something called wicd. 

I'm still a total newb (had linux installed for less than 72 hours). So I'm not sure if I'm getting myself in over my head here but do you all think that this will work? If so, is there a guide on how to do this?

I downloaded the latest version (1.46) from the website and opened the documentation. It said to use the "make" command in terminal. i did so but got a whole bunch of error messages. I also looked at the Ubuntu documentation site but didn't see anything about compiling programs. 

Please, please, someone help!

---

### Post by plinydogg on 2007-06-07
Okay, I started trying to think outside the box and looked at ndiswrapper instructions for other cards. I found this, which I think will show me how to compile the latest version of ndiswrapper:

[http://ubuntuforums.org/showthread.php?t=464720&highlight=easy+ndiswrapper](http://ubuntuforums.org/showthread.php?t=464720&highlight=easy+ndiswrapper)

So, my question now is, do you guys think this will fix the problem? And if not, do you have any other ideas?

---

### Post by kevdog on 2007-06-07
From the ndiswrapper website, lookup your card from their "list" of support cards, and download the driver they recommend for your card.  I found my windows drivers that I had on CD didnt work either, but the drivers from the ndiswrapper website did work!!

---

### Post by plinydogg on 2007-06-07
kevdog: thanks for the respones! Do you mean the driver they recommend or the version of ndiswrapper they recommend? THANKS!

---

### Post by plinydogg on 2007-06-07
Kevdog: I did as you suggested and went here:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/)

But there are a ton of entries for my card (BCM4318)! Any advice?

Thanks in advance!

---

### Post by kevdog on 2007-06-07
No the driver they recommend for your card.  Here is how you choose what you want.

First issue 
lspci

Take note of network controller -- Here is what my network controller looks like:
06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Notice the 06:00.0 number (or whatever  your number is).

Then type lspci -n and find the line that starts with 06:00.0 (or whatever your number is); This is mine for example:

06:00.0 0280: 14e4:4320 (rev 03)

With this number 14e4:4320 (substitute your number), your name of your card and model (D-link,linksys) and chipset (Broadcom rev 03 in my example), you should be able to find the correct driver from the ndiswrapper list.

Hope that helps!

---

### Post by rpg36 on 2007-06-07
I'm having the same problem with the same network card. a Broadcom 4319. I found a guide that does get the wifi working but there is a serious problem with it. After following the instruction in the <a href="http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset">unofficial </a>ubuntu guide the wireless works great untill i turn of ubuntu. After turning it off It won't restart, it freezes while it is loading up and comes up with an error that says something like bcm43xx fatal error  fatal DMA error. I haven't tried using DNISwrapper with the drivers from their site, only with the drivers i have. Will the drivers from their site make it work and do i need to blacklist the bcm43xx driver?

if the html link doesn't work the website for the guide is this [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)

---

### Post by kevdog on 2007-06-07
I hate questions like the one above.  Not meaning to be rude, but how the heck do I know if it will work.  No one can give you any assurance that ndiswrapper will work -- but since the bcm43xx installation doesnt work, do you have anything to lose!

---

### Post by rpg36 on 2007-06-07
I know you can't guarantee ndiswrapper will work but any advice on the bcm43xx fatal error fatal DMA error when i try to start up ubuntu after installing the drivers as directed in the unofficial ubuntu guide and me having to reinstall ubuntu 10 times in the past two days? Its sad but i'm seriously getting to the point where i might just switch back to windows on my laptop if i can't get this figured out :(

---

### Post by kevdog on 2007-06-08
I dont know anything about your wireless card as far as revision or chipset, but have you visited the bcm43xx to see if your card is even supported?? [http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)

If its not supported, then you really have no choice but to install wireless drivers with ndiswrapper.

---

### Post by rpg36 on 2007-06-08
Through days and days of digging I have finally gotten my Broadcom 4318 wireless card to work. There are two things that really helped me out a lot that might be useful here. Download the drivers from the ndiswrapper website, they are the only ones i could get to work. Also, for me at least, and a few other people ndiswrapper will not work with the newest kernel version. 
Here is a link to the ndiswrapper site that has many different drivers for broadcom wireless cards [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/) 

here is a link on how to downgrade your kernel to the previous version which I had to do in order to get ndiswrapper working [http://ubuntuforums.org/showthread.php?t=465981](http://ubuntuforums.org/showthread.php?t=465981)

I hope this info can help.

---

### Post by plinydogg on 2007-06-08
Thanks rpg36, but there are a million broadcom 4318's listed on that link. How do you know which one to grab. Thanks for the tip about downgrading the kernel. I'll give that a try too. Thanks again.

---

### Post by plinydogg on 2007-06-08
Okay, the drivers I need from the ndiswrapper page are for 14e4:4318 (rev 02). The problem is that the file that is available for download is an .exe file, which can't be opened on Ubuntu unless I get some special software. Where do I get this software? I can't get it using apt-get because I don't have Internet access....

---

