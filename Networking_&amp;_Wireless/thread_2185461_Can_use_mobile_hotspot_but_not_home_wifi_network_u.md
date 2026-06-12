---
title: "Can use mobile hotspot but not home wifi network ubuntu 13.10"
date: 2013-11-02
forum: Networking &amp; Wireless
---

### Post by sbadger91 on 2013-11-02
Hi everybody,

I am fairly new to linux. I orginally installed mint 15 mate on my laptop a few months ago. Now I have installed Ubuntu 13.10 on my desktop. I have no access to ethernet where I am so I been using a USB adapter for a couple years on Windows 7. Anyway, when I attempt to connect to my home wifi network with my TP-Link TL822N it will just continously ask me for my password even though it is correct and it never actually connects me to my wifi network. I have been able to connect to my mobile hotspot but even that is pretty unreliable; most of the time the internet comes and goes. 


Just FYI I have ubdated my system with the updater and installed ndiswrapper with the synaptic package manager.

I also tried this thread[ http://ubuntuforums.org/showthread.php?t=885847]("http://ubuntuforums.org/showthread.php?t=885847")

All though when I type this nothing comes up in terminal. It doesn't indicate whether I have a bad driver or not. 
>  ndiswrapper -l

Any ideas or solutions to this?

Thanks.

---

### Post by syam-nair on 2013-11-03
cross check the modem configuration. If the modem is home use, I suggest WPA encryption, to avoid errors. WEP and others can make complications if not properly configured.
Also if it can conect to mobile hotspot, then there should be no driver problems.

---

