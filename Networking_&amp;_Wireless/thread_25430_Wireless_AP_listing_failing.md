---
title: "Wireless AP listing failing"
date: 2005-04-10
forum: Networking &amp; Wireless
---

### Post by Klin'Targ on 2005-04-10
I am using a Linksys Instant Wireless WPC11 (v3) card to access my wireless network. I want to scan for a list of APs, but when I issue this command:
```
sudo iwlist eth1 scan
``` I get
```
eth1      Interface doesn't support scanning : Operation not supported
```
Any ideas? I never got this working in gentoo either, so it may be that the Linux drivers for my card don't support this. It does, however, work in windows.

---

### Post by accuser on 2005-04-11
Firstly, is eth1 really the interface for the WPC11? Try:
```
$ sudo iwlist scan
```
to check all interfaces. The fact that eth1 does not support this suggests that it is not infact the correct interface.

Secondly, and this is why I asked my first question, are you using ndiswrapper? If you are then are you using the correct ndis driver? The one that ships with the card (i.e. on the CD) is no good. Get [this](http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180)  instead.

If you are using the ndiswrapper, and you have the correct ndis driver installed, then it is likely that your interface is actually wlan0.

---

### Post by Klin'Targ on 2005-04-11
[QUOTE=accuser]Firstly, is eth1 really the interface for the WPC11?[/QUOTE]Yes. I have eth0 for my wired connection and eth1 for my wireless. A scan of all interfaces yields something akin to
```
lo        Interface doesn't support scanning
eth0      Interface doesn't support scanning
eth1      Interface doesn't support scanning : Operation not supported
```
[QUOTE=accuser]Secondly, and this is why I asked my first question, are you using ndiswrapper? If you are then are you using the correct ndis driver? The one that ships with the card (i.e. on the CD) is no good. Get [this](http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180)  instead.
If you are using the ndiswrapper, and you have the correct ndis driver installed, then it is likely that your interface is actually wlan0.[/QUOTE]
I am using the orinoco driver, not ndiswrapper. I will try ndiswrapper if it has better support, but everything except scanning works with the orinoco driver.

---

### Post by Klin'Targ on 2005-04-19
I am now trying to use ndiswrapper, however I cannot seem to get my card recognized by the driver. Any suggestions? I have used the driver provided in the link and edited the .inf file's pci-id as directed to on the ndiswrapper site, but ndiswrapper -l just shows ```
Installed ndis drivers:
net8180 driver present
```

---

### Post by tebibyte on 2005-09-15
Hi. I had the exact same problem when using NdisWrapper. Can someone revive this topic, and assist us in figuring out the situation. There may be even others who have the same problem.
Note: i'm pretty much a newbie.  :???:

---

### Post by tebibyte on 2005-09-19
Would someone please reply.  ](*,)

---

### Post by mlomker on 2005-09-19
> Would someone please reply.

I did a few Google searches on the adapter and it doesn't sound like it works completely on any version of linux.  I think you should buy a different adapter if you need full functionality.  Adapters are getting cheap these days.

---

### Post by tebibyte on 2005-09-20
Thanks. I'll try that out then. :neutral:

---

### Post by hil on 2005-11-20
Check if your Linksys WPC11 uses the right driver. [http://forums.fedoraforum.org/showthread.php?t=74044]("http://forums.fedoraforum.org/showthread.php?t=74044")
In my scenario, I have to ifconfig eth1 192.168.0.5 (supposing your access point IP is 192.168.0.1). iwconfig eth1 essid default (suppose your access point essid is "default"). Then you can ping -c 3 192.168.0.1. Make sure your eth0 is not in 192,168.0.0 network. My built-in wireless card does not support scanning but I can connect to the access point.

---

### Post by mlomker on 2005-11-20
[QUOTE=hil]Make sure your eth0 is not in 192,168.0.0 network. My built-in wireless card does not support scanning but I can connect to the access point.[/QUOTE]

That'd be a problem if they both have a default route on them.  There's a command-line tool called **ifmetric** that'll allow you to configure which one to prefer.  I've used it in a couple instances.

---

