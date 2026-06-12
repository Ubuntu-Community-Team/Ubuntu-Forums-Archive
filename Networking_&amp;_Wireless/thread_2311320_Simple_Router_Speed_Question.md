---
title: "Simple Router Speed Question"
date: 2016-01-26
forum: Networking &amp; Wireless
---

### Post by echotech2 on 2016-01-26
I have a D-Link DI-604 router which is rated at 10/100 Mbps. The firmware is dated 18 April 2007.  Connected to the router are the computer and a printer via ethernet cable. 

  I currently have 10 Mbps service from my ISP but this is being upgraded to 30 Mbps.

  I guess the real questions are: Will this router allow me to get 30 Mbps? What does 10/100 Mbps mean?  100 Mbps computer to router, 10 Mbps to ISP, vice versa, upside down, backwards?  Or am I totally off the track?

  No, I don't know much (anything?) about networking.

---

### Post by chili555 on 2016-01-26
> Or am I totally off the track?Yes, exactly.

Ethernet cards are typically rated to negotiate and connect at 10 Mbps, 100 Mbps and 1000 Mbps. Here are the details from my own card; from the terminal:```
sudo lshw -C network
```> *-network               
       description: Ethernet interface
       product: Ethernet Connection I217-LM
       vendor: Intel Corporation
       <snip>
       capabilities: pm msi bus_master cap_list ethernet physical tp [COLOR="#FF0000"]10bt 10bt-fd 100bt 100bt-fd 1000bt-fd [/COLOR]autonegotiation

So my ethernet card, and i assume yours, will negotiate and connect with an access point, usually a router, at any of those speeds. 'fd' refers to duplexing. Half duplex means that the router speaks and the ethernet card may only listen. Full duplex (fd) means that both may speak and listen at the same time. Most modern equipment will do 100 or 1000 Mbps at full duplex.

There are tinkerers like me that delight in digging some old crusty circa-1995 laptop out of the dumpster and having a peek at what's inside; we need to know about 10 Mbps at half duplex!

I suspect that your ethernet card does 100 Mbps full duplex easily and that, assuming your wiring is good and except for a tiny bit of overhead, you will see 30 Mbps at your computer.

---

### Post by echotech2 on 2016-01-26
Thanks for the enlightenment and assurance, chili555.  Lots of numbers that mean little to me.

```
 *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       ..........................................................
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.100 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s



```

---

### Post by chili555 on 2016-01-26
> 10bt 10bt-fd 100bt [COLOR="#FF0000"]100bt-fd[/COLOR] 1000bt 1000bt-fdSo your ethernet card will negotiate and connect at 100 Mbps full duplex and above.

As I said, assuming your wiring is good and except for a tiny bit of overhead, you will see 30 Mbps at your computer. Think of this as a freeway where the speed limit is 100 mph. You are getting a new car that will do 30 mph. Will your car achieve 30 mph on a 100 mph freeway? Certainly.

There are two cautions I can think of. First, there is a certain amount of overhead in data transmission: [https://en.wikipedia.org/wiki/Fast_Ethernet#100BASE-TX](https://en.wikipedia.org/wiki/Fast_Ethernet#100BASE-TX) > The MII fixes the theoretical maximum data bit rate for all versions of Fast Ethernet to 100 Mbit/s. The data signaling rate actually observed on real networks is less than the theoretical maximum, due to the necessary header and trailer (addressing and error-detection bits) on every frame, the occasional "lost frame" due to noise, and time waiting after each sent frame for other devices on the network to finish transmitting.Second, while the advertised *down*load speed is 30 Mbps, the upload speed may be different.

Have fun! Where I live out in the woods, I'd love to have even 10!

---

### Post by echotech2 on 2016-01-26
Once again, thanks for the information.  I was just wondering about my old router.  It's been sitting under my desk undisturbed doing it's thing since about 2008.  The rest of the computer is almost the same age.

---

### Post by chili555 on 2016-01-26
My router was old when you bought yours!!

I say, if it ain't broke, don't fix it. I'd wait for the upgrade and if you get good speeds, pat your little router on the head and tell it thanks for being a good router. I suspect that will be the case.

---

### Post by echotech2 on 2016-01-26
How old does it have to be to have antique value?

---

### Post by echotech2 on 2016-02-25
Update...

  Tech came, installed new modem for 30Mb/s.  Speed test showed 10Mb/s, not good.  Bypassed router, full speed.  Went into router setup (Tech!, not me, lol).  Entry below was set to 10Mb/s/full, reset to 100Mb/s/Full and Viola!! all is well.  

  WAN select to 10/100 Mbps
  	100Mbps/Full 
        10Mbps/Full 
        10/100Mbps Auto

---

### Post by FaultedGeologist on 2016-02-26
Should you want to upgrade the firmware, that is a fun journey for the first timer!  I am beginner/intermediate, but I did this years ago to get better results.  I think there have been some upgrades in wifi security since then, and you definitely want to change the default router password.  

Type in the router model and firmware, then follow the instructions from the mfg website:

[https://www.google.com/search?q=D-Link+DI-604+firmware](https://www.google.com/search?q=D-Link+DI-604+firmware)

---

