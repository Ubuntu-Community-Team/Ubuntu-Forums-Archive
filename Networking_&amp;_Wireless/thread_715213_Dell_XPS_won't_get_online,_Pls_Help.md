---
title: "Dell XPS won't get online, Pls Help"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by mlyons16 on 2008-03-04
Hey all,

I have a Dell XPS M1330 with the Dell 1505 Draft 802.11n WLAN Mini-Card.  When I boot up into the Ubuntu 7.10 Live CD there is no option for wireless connections. I only can connect via a Wired Connection (Ethernet cable). 

I've heard of ndiswrapper, is that the appropriate solution for this problem.

Someone please help me. I really want to get my XPS on Linux, but I rely on wireless.

Thanks in advance.

---

### Post by uberlube on 2008-03-04
Yes ndiswrapper is the way to go. Once you have ubuntu installed on your system you will need the windows version of the drivers on CD or you can download them from their website. Once you got that you can use ndis to extract the firmware from the drivers and install them. If you have any questions about using ndis, check out this thread its the best:

[http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper)

---

### Post by mlyons16 on 2008-03-04
Okay, I believe I found the driver at:

[http://support.dell.com/support/downloads/driverslist.aspx?os=WLH&osl=EN&catid=5&impid=-1&servicetag=&SystemID=XPS_M1330&hidos=WLH&hidlang=en](http://support.dell.com/support/downloads/driverslist.aspx?os=WLH&osl=EN&catid=5&impid=-1&servicetag=&SystemID=XPS_M1330&hidos=WLH&hidlang=en)

It's the 7th row down, and says it applies to my exact wireless network adapter model. So I should download that file?

I'll put it on a USB key and then can I use it? And is that the proper driver do you believe?

---

### Post by uberlube on 2008-03-04
Yup if it says its your chip grab it. Can you make a wired connection to your laptop? It will make the process alot easier if you can cuz youll need to download ndiswrapper from the repos.

---

### Post by mlyons16 on 2008-03-04
Yep, I can certainly make a wired connection.

I just add those in Synaptic under Repositories > Third Party Software or Software Sources or something.

So I should actually install 7.10 first, and then go from there?

---

### Post by uberlube on 2008-03-05
Yes you actually have to have ubuntu installed on your hard drive to get your wireless working cuz you'll have to reboot after you set it all up to get it to work. And that obviously wont do you any good if your just working off the live cd.

---

### Post by mlyons16 on 2008-03-11
Hey, so would these instructions about using ndiswrapper apply to Ubuntu derivatives, particularly Kubuntu?

---

### Post by mlyons16 on 2008-03-29
Hi, so I used the command:

```
 lspci 
``` in the terminal, and I got the output: ```
 0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03) 
```

I came across a document at:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

This says that the driver for the wireless network adapter should be in Restricted Drivers Manager.. It's not. I don't know if running a software update would help, and maybe bring this driver come into existence or not.

I've enabled all the software sources, all the update sources, etc and there are 253 updates that can be installed. I'm not sure if the bcm43xx -fw cutter package is on the list or not tho.

Can someone help me before I have to give Ndiswrapper a try?

---

### Post by mlyons16 on 2008-03-29
Hi, so I tried the installation documentation at:

[https://help.ubuntu.com/community/Wi.../bcm43xx/Gutsy](https://help.ubuntu.com/community/Wi.../bcm43xx/Gutsy)

but, I was not successful. Mind you, I am running off the Live CD (but I don't think that matters since there is no reboot instructions. I do have a working Ethernet connection so I was able to follow the instructions very accurately, but still nothing is coming up to enable any driver for the wifi under RDM). I'm also thinking that maybe since my laptop's wireless adapter is so new and cutting edge, by having N support as well, that maybe that  bcm43xx-fwcutter driver simply isn't meant for the latest and greatest of Broadcom wireless cards. 

Next step, use the latest driver I can find for Windows and make that work with Linux via Ndiswrapper.

Any thoughts, any one?

---

