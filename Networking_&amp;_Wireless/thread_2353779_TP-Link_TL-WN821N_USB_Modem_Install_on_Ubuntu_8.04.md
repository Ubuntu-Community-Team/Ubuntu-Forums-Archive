---
title: "TP-Link TL-WN821N USB Modem Install on Ubuntu 8.04 / Acer 3003 Notebook"
date: 2017-02-24
forum: Networking &amp; Wireless
---

### Post by afz12 on 2017-02-24
Hi All

I've recently got an old Acer 3003 notebook to run again and it now dual boots Ubuntu 8.04 and 12.04 (not higher). I can use a TP-Link TL-WN821N WiFi modem on 12.04 but not on 8.04 - it seems that the dkms module isn't available?

I installed its internal b43-fwcutter based WiFi modem commands and it seemed to accept these and the front lead lights up showing the hardware is available. However it won't connect to the Internet using this (Ethernet connects fine though). Also the USB TL-WN821N dongle doesn't work at all in this old OS.

I am looking for either of two possible fixes - can I get the notebook's internal modem to work (it may be incompatible with my router though - I don't want to change any settings in case this upsets other notebooks) or can anyone suggest any commands I can paste into a terminal to make the USB WiFi modem work in Ubuntu 8.04

 The TP-LInk website has a download for the WN821N as a zip file that opens as a windows install and certainly won't work. Any suggestions are welcome :P

---

### Post by mörgæs on 2017-02-25
First of all I think you should get rid of the old software. What happens if you try to boot from Lubuntu 16.04.2?

---

### Post by afz12 on 2017-02-25
Hi mörgæs

Thanks for your reply. The Acer 3003 notebook is quite old but is still useful - I use it to run BOINC projects e.g. SETI. Its screen hardware will support Ubuntu 12.04 but higher versions are beyond it. It will boot from Ubuntu 12.04 by itself but its internal modem is not recognized - despite having installed b43-fwcutter for this OS. It only indicates a presence in Ubuntu 8.04 (and 8.10 as a live CD) but not on higher OS. I would prefer to keep 8.04 if it can use the internal WiFi modem as this frees up my USB One.

I know this is a fairly petty request as this old notebook is one toss away from the recycle bin but it could be useful for science re BOINC computations in a spare room I never use:D

My other motivation is to learn a bit more about Linux in general so for me this is a learning exercise mörgæs

---

### Post by mörgæs on 2017-02-25
I understand your desire to keep the old fella running. See the link in my signature for more advice on the topic.

It does not surprise me that Ubuntu is too heavy but what about Lubuntu?

---

### Post by afz12 on 2017-02-25
Hi mörgæs

Thanks for the suggestions - and yes I like to keep the old H/W in pace with the new. However this '3003 notebook has its share of cobwebs and doesn't respond well to CD installations - (DVD no, but does OK on Ubuntu 12.04 on a USB optical drive with a DVD disk). Also I have tried several time with alternative installs - these always fail 1/2 way through, the only option that works is the immediate one presented! Installing Lubuntu will only work as a third partition - from past experience doing anything different will fail on it and even so, wiping all and doing a full install might be the only option anyway.

It may be the case that the internal modem WiFi will never connect to my home router - if so the Ubuntu 8.04 may as well be wiped as storage space. Ubuntu 12.04 works OK on it and the external USB WiFi dongle appears to be supported.

I don't mind installing new OS - do you suggest Lubuntu 12.04 mörgæs?

If it needs the external USB dongle then so be it I guess. So far it has completed some BOINC projects, despite being an old single core CPU with only 384 MB of RAM!

---

### Post by gordintoronto on 2017-02-25
The memory is not sufficient for any modern Ubuntu-based Linux. By running ancient versions of Linux, you are opening yourself for exploitation.

You might have a look at Tiny Core Linux or Damn Small Linux.

---

### Post by afz12 on 2017-02-25
Hi gordontorono

Thanks for your suggestions - I'll look at these smaller OS, they sound interesting. However I feel your concerns are unwarranted. This old notebook does run Ubuntu 12.04 fine and has been computing work units for BOINC distributed computing projects for the last few days and connects to the Internet quite well using a USB dongle (TP-Link TL-WN821N), despite being a bit shy on RAM. I recovered its OS recently otherwise it would have been sent to a recycle center but now that it is going it can make some contribution to science, running BOINC projects 24 / 7 until such time as it finally expires.

When it boots into Ubuntu 8.04 the internal modem indicator led operates, suggesting the modem hardware is OK. However it doesn't respond on Ubuntu 12.04 OS. I would prefer to find a way to make its internal WiFi modem to work with my router (supplied by my service provider with WPA2/WPA-PSK TKIP-1 AES) but I don't want to interfere with the router's settings as this may upset WiFi communications with other notebooks and devices. I would prefer to release the USB modem if possible in case other notebook's eventually loose their internal WiFi modem hardware. Also I am curious to try out code in the terminal.

If anyone has constructive suggestions on how to make the internal modem work on this notebook on Ubuntu 12.04 then I am interested to read:P. However it is not an important issue - certainly I can't see any possibility of "exploitation" given my planned usage for it - so if no answers to my question are forthcoming in the next few days, I'll mark the post as "solved" (i.e. as solved as it could have been) and leave it at that. :KS

---

### Post by mörgæs on 2017-02-26
> **gordintoronto said:**
> 
You might have a look at Tiny Core Linux or Damn Small Linux.

Tiny Core is an option but Damn Small Linux should be avoided (and forgotten) for the same reasons as Ubuntu 8.04: It's an abandoned project which has not received bug fixes for years.

---

### Post by Irihapeti on 2017-02-26
I don't know too much about BOINC projects, but could they be done from the commandline? That wouldn't need a huge amount of resources.

---

### Post by afz12 on 2017-02-26
[**[COLOR=#DD4814][B]Hi mörgæs**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=939075") and [**[COLOR=#C61919][B]Irihapeti**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=346442")

 Excellent advice. Anyway I am happy with the USB modem as a fix - I am just an old scientist / mathematician at heart I guess so letting this old notebook roll on and contribute something to science via BOINC is worthwhile. I like the SETI, Einstein and LHC initiatives. I have another Acer 5920 that is getting ready to contribute also.

Thanks, I'll mark this thread as solved.

---

### Post by mörgæs on 2017-02-26
> **afz12 said:**
> 
Thanks, I'll mark this thread as solved.

Good, please use Thread Tools for that.

---

### Post by kurt18947 on 2017-02-26
Your hardware is a youngster:D. I have an HP desktop that was born with Windows ME in 2000. It came with 64 MB. RAM and original Celeron 660 Mhz. processor. I did upgrade the RAM to 512 MB. and added an Ebay ISA Nvidia video card. I tried different *buntu distros but couldn't get them to install, due I think to video issues. This machine is currently running MX linux (google it)  functioning as a Torrent box serving up a few different smaller linux distros. MX linux is billed as a mid-weight distro but it seems pretty light for a GUI distro.

---

