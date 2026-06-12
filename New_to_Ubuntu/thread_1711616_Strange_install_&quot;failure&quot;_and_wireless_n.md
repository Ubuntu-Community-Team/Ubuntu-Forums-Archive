---
title: "Strange install &quot;failure&quot; and wireless not working"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by gnarlygnarlingtons on 2011-03-21
I just purchased and installed Ubuntu 10.10 maverick meercat on my Dell xps with intel core 2 duo processor and something strange happened. I left the room as it was installing and came back later to find the message "we're sorry, but the installer failed" so I rebooted the computer to find nothing but a screen of black and white lines and TV antenna style static. I thought my computer was fried, so I took the disc out and rebooted again hoping that my windows 7 partition was still intact. What do you know, but the dual boot selector screen came right up and ubuntu seems to work just fine. In fact I'm using it now. What kind of "install failure" was that? Am I going to have some unforeseen problems or can I keep using it as installed? I have found no problems so far.

Also, I have not been able to pick up my wireless router on ubuntu, either on the live disc or installed. The message under my wireless networks application is "device not ready-firmware missing." What type of firmware it doesn't say, nor does it tell me where I can get it. The only way I can currently connect to the internet is plugged directly into the back of the wireless router. How can I fix this?

Any help is very much appreciated as I am a total linux noob and not computer programming savvy.

---

### Post by gnarlygnarlingtons on 2011-03-21
Anyone have any experience with this issue?

---

### Post by synapsys on 2011-03-21
It sounds like your wireless card is not supported in the kernel by default. There is a Wireless forum here just for problems like this. You may want to post there for a quicker response. The first thing you're going to want to do is run this command in a terminal:

```
lspci
```

This will list the make and model of your wireless card (among other things) if it is recognized by the OS. You also may want to re-install and watch what happens this time. This problem could be related to that error.

---

### Post by gnarlygnarlingtons on 2011-03-21
Thanks a lot. I'll try that. Noob question-how do I get to these command terminals that I hear everyone talking about? 
Also my wireless card is a Dell  wireless 1390 WLAN mini card if that illuminates anything.

Man I would hate to have to reinstall everything. It took hours for the upgrades to download and install.

---

### Post by gnarlygnarlingtons on 2011-03-21
Okay I think I am close to resolving this problem. I entered the command and found out that my WLAN card is a Broadcom BCM4311. I also notice that there are two drivers available from the additional drivers app that seem to support this model, the Broadcom B43 and the Broadcom STA wireless drivers. Which one of these should I download, or do I need both? 

Thanks so much for the help.

---

### Post by gnarlygnarlingtons on 2011-03-21
Nevermind. I answered my own question. Googled B43 vs STA and found that most people find the STA to be better so I downloaded it and now my wireless works great. Easy as pie. Problem solved.

---

### Post by synapsys on 2011-03-22
> **gnarlygnarlingtons said:**
> Nevermind. I answered my own question. 
I love it when that happens. :D

Glad you got it working.

---

### Post by grahammechanical on 2011-03-22
As regards that strange install failure message ... at the end of the install process we usually get a message to remove the CD from the drive and press any key to reboot. I have never waited long enough to find out what would happen if I never pressed a key to reboot. I think that you have found that out for us.

Regards.

---

