---
title: "New install of Edgy, no connection to network, internet"
date: 2007-03-27
forum: Networking &amp; Wireless
---

### Post by scatfly on 2007-03-27
I just installed edgy on an old dell dimension and can not connect to network or internet.  I have another ubuntu box that works fine so i used the DNS addresses from that one, but that did not help.   Could not reach 192.168.1.1, when i tried in firefox.  I have DHCP enabled both on the machine and router.  any ideas?

---

### Post by atomic_turtle on 2007-03-27
Hello scatfly,

ideas? Many - too many at this stage:
- Is your network card supported?
- What method do you use to connect?
- Wireless or LAN?
- how does your /etc/network/interfaces look like?
- What does iwconfig tell you?
You see, there can be a wide variety of reasons why a network connection doesn't work - mine was my personal Ubunightmare for a long time, so I daresay I've been through a couple of them which doesn't mean I'm an expert now and I'm not saying that.
What I'm saying is: The more information you have before you post a question and the more detailed you can describe your problem, the better the chance of a usable answer.
The Wikis are a good place to start. There's plenty of information there on network problems and standard tests you can do to get more information on your particular problem. On one Linuxboard, I even found a script someone had written with a whole set of network tests - unfortunately I don't have the link anymore.
HTH.
Best regards,

atomic_turtle

---

### Post by scatfly on 2007-03-27
In the device manager it says something about compatible 10/100, so i take it my nic is good.  I am wired (wire is good) to the LAN.  

etc/network/interfaces gave me this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan inet dhcp
```

iwconfig gives me no wireless extions for the ones listed

---

### Post by atomic_turtle on 2007-03-28
Hello scatfly,

as a relativ (K)ubuntu newbie, I'm already entering thin ice here, but here's what I think:

- What the device manager tells you doesn't necessarily mean a thing. It can well be that your device is being recognized, but that doesn't say it works - happened to me with a USB wireless adapter: Kubuntu told me it was there, even told me the brand name and all, but still it wouldn't work. What chipset does your card use? 

- That iwconfig doesn't list any wireless extensions points in the same directions as what I said above - but you're not looking for wireless, are you? Maybe iwconfig is only for wireless, I'm not sure here - as I'm no "real" forum admin, I don't have a box of links to quickly look stuff up, it would take me as much time as you. Try ifconfig, maybe...

- I rather think that what you see in your /etc/network/interfaces is the standard that's always there when you install your system. For your LAN to be configured (should be eth0 if you've got only one network card), there should be figures like the SSID and the logon data, if any.

But, as I have only ever configured a wireless LAN (which looks a bit different) and I did that with a lot of help from the forums, this is really the point where I have to - and I do - admit that I can't be of further help for you. I can only advise you to have a look in the Wikis (I only know the German one at ubuntuusers.de, the general wikipedia also holds a lot of stuff on all flavours of Ubuntu, there's literally tons of information out there) or ask the experts. In the German webspace, there's a project called like "linux godfathers" - you get the idea: It's someone specifically selected to guide and help you who you can ask any questions via email or chat. Very helpful for beginners.
I hope this will help you a bit further along. Don't let yourself be demoralized by difficulties like this - configuring a Linux system is not as easy and convenient as with Windows, but it's worthwhile.
Best regards,

atomic_turtle

---

### Post by atomic_turtle on 2007-04-18
Hi scatfly,

solved your problem? (If so, it wasn't me ;-)
Regards,

atomic_turtle

---

