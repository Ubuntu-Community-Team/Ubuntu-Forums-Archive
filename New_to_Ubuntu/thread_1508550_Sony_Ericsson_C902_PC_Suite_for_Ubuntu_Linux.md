---
title: "Sony Ericsson C902 PC Suite for Ubuntu Linux"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by mungatsuma on 2010-06-13
I just installed Ubuntu Linux Lucid but cannot access the internet. I have been utilising my Sony Ericsson C902 PC Suite for internet connection but the available software from the manufacturer is Windows based. I need the internet o configure, watch DVD movies, listen tomusic and generally add the software I need to customise my desktop and Ubuntu but am at a Fix. Please help me out.:confused:

---

### Post by slash86 on 2010-06-13
Hi,

i have a nokia 5530. Nokia PC Suite (just like sony ericsson) is just for windows. I guess you will not be able to use PC Suite on any linux distribution, including ubuntu. Concerning you internet conection how did you connected to internet on windows? is it a wireless card? If the problem is your internet connection, please, give some information that can help on solve that.

---

### Post by khelben1979 on 2010-06-13
Are your mobile phone connected to the PC by [USB]("http://en.wikipedia.org/wiki/Usb"), [bluetooth]("http://en.wikipedia.org/wiki/Bluetooth") or something else?

---

### Post by flyfishingphil on 2010-06-13
> **mungatsuma said:**
> I just installed Ubuntu Linux Lucid but cannot access the internet. I have been utilising my Sony Ericsson C902 PC Suite for internet connection but the available software from the manufacturer is Windows based. I need the internet o configure, watch DVD movies, listen tomusic and generally add the software I need to customise my desktop and Ubuntu but am at a Fix. Please help me out.:confused:
I have the SE W760 and, yes, everything is written for Windough$ so it doesn't work with Linux. I tried the WINE, but don't waste your time with that. I found that WINE is designed for games and doesn't do much else at all well. if at all.

I have taken the time though to get the latest Virtual Box, available at:
[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads"), install that in 10.04, do a little fine tuning and everything works great. 

If you do this you will also need a copy of Win XP because the Sony Ericsson doesn't work with much newer than that.

Easy instructions to follow on VBox, they are identified as to which one to download for Ubuntu, and you can do a direct download/install. Just don't ask me what all I did to get everything operationalbecause I don't remember everything. I do remember though that it was something simple. along the lines of activating something in Ubuntu, that finally got it fully operational. (I'm new at this so not a good guide to what needs to be done.)

Hope this helps.

---

### Post by khelben1979 on 2010-06-13
The only thing he/she needs is a working internet connection from the mobile phone and since he/she has posted to the newbie section, I wouldn't recommend VirtualBox.

Ubuntu Lucid has a pretty modern Linux kernel which will hopefully identify the mobile phone and if the modem inside the phone can be used by Ubuntu, then problem has been solved.

---

### Post by Locke_99GS on 2010-06-13
Plug your phone into the Ubuntu PC. Just click cancel if it wants to mount the media card on the phone. Open "**System -> Preferences -> Network Connections**", select the "Mobile Broadband" tab, click "Add", then follow the prompts to use your phone's internet connections from the PC. At the end of the wizard, at the top, check "Connect automatically".

I went through these steps just now and set up my Sony C905. I just submitted this post on Ubuntu with AT&T 3g internet through my phone.

edit: See notification bubble in attached screenshot.

---

