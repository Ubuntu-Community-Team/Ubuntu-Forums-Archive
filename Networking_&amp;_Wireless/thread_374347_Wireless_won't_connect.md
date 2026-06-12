---
title: "Wireless won't connect"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by JonD25 on 2007-03-02
I tried searching for a solution, but no luck.

I have a Dell Latitude D600 with a bcm4306 wireless card. I followed [this guide](http://www.ubuntuforums.org/showthread.php?t=340689&highlight=tutorial+ndiswrapper) to get ndiswrapper working. I then used [this guide](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show#head-fc5c0a6119d42dad8a33abbeb0d25d4d3c35d8c1) to get Network Manager working. Both seem to be working fine, except one problem. It won't let me connect. I don't know if it's a problem with my computer or my network (I'm on my school's wireless network), but it just won't connect. Network Manager tells me there's the wireless network there for me to connect to, so when I click on it to connect, it does the spinning graphic to show that it's trying to connect, and eventually just stops trying. While Ubuntu isn't exactly new to me, I'm certainly still a beginner. So any help you guys can give me would be great.

I also forgot to mention that I am using Edgy with all the latest updates, if that matters.

---

### Post by JonD25 on 2007-03-03
Anyone?

Another detail, I'm using ndiswrapper-1.37, not 1.34 like the guide I used said.

---

### Post by CrazyTn on 2007-03-03
Have you tried connecting without Network manager?

Go to administration->Networking

Go to property, put in the network name and password(if there is one)
then enable wireless

Maybe that will work, might be NM that is messing up

---

### Post by Prometheus.172214 on 2007-03-03
Does the wireless network that you are trying to connect to, use any wireless encryption? You might need to do what was said before of going into Networking and entering the ESSID and the Hex key / Pass key for the network. 

The second article that you referred to talks about WPA Support for the wireless controller to be enabled via a series of commands, it can be possible that this program does not support a particular encryption protocol. You could give alternate programs like Wireless Assistant or Wireless Radar a try.

---

### Post by JonD25 on 2007-03-03
Got it to work. It's not encrypted, so it wasn't that. I just did what CrazyTN suggested and used Networking instead. So now it works.

It's weird though, because I've gotten Network Manager to work before on a previous installation of Ubuntu. But when I reinstalled and went through the whole ndiswrapper thing again, suddenly it doesn't. Oh well.

---

### Post by Prometheus.172214 on 2007-03-03
Great to know it is working :-)

It drove me nuts when it did not work on mine and I had to do what you did.

---

### Post by CrazyTn on 2007-03-04
> **JonD25 said:**
> Got it to work. It's not encrypted, so it wasn't that. I just did what CrazyTN suggested and used Networking instead. So now it works.

It's weird though, because I've gotten Network Manager to work before on a previous installation of Ubuntu. But when I reinstalled and went through the whole ndiswrapper thing again, suddenly it doesn't. Oh well.

Network manager doesn't even detect my wireless card, so I end up using wifi radar instead.

---

