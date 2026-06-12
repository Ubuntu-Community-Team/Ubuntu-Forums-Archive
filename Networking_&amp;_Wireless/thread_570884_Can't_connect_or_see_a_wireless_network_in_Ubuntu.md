---
title: "Can't connect or see a wireless network in Ubuntu"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by Nehvrook on 2007-10-08
Hi all. I've never tried wireless myself, always prefering wired connections for simplicity. But my Dad just the other night installed Ubuntu. He uses a laptop and dual boots with Windows Vista. We know the network is set up properly and everything because we can connect in Windows.

So the problem is, we have no idea how to get Ubuntu to connect to the wireless network. I bought a magasine which was dedicated to helping people setup Ubuntu. Under the wireless networking section in there it says that he should use the System > Administration > network tool and it should auto-find a list of wireless networks in range. We tried this and it did not work. We also tried entering the SSID and WEP key in as many places as we could and it still wouldn't pick anything up.

I've googled and searched these forums and I can't seem to find any similar problems so I thought I'd ask if anyone can see a problem or give us any advice on where to start, or a link to a howto to address this problem.

---------------

Here is some relevant information

He is running Ubuntu 7.04 from a live CD made a few months ago (Would using a network cable to connect to the net and updating Ubuntu help?)
The wireless network card he is using is built into the laptop and didn't come with any drivers (They may have already been installed on Vista when he got it, but there was no driver disk to go with it)
I think the name of the wireless card is "AirForce One 54g"

Looking around the forums I tried a few commands and got this in a terminal output which may be usefull. (I actually had my dad get this for me and it looks like he might have missed something relevant out when copying and pasting but this is all I have for now)
```
              configuration: broadcast=yes driver=b44 driverversion=1.01 latency=64 multicast=yes
                resources: iomemory:d0000000-d0001fff irq:21
           *-network:1 DISABLED
                description: Wireless interface
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@06:02.0
                logical name: eth1
                version: 02
                serial: 00:19:7d:8c:4a:53
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 multicast=yes wireless=IEEE 802.11b/g
                resources: iomemory:d0002000-d0003fff irq:22
           *-pcmcia 
```

And the attached image is a screenshot of his device manager.

Thanks for any help and taking the time to read the problem

---

### Post by scrooge_74 on 2007-10-08
Ok, a couple of things.

Are you running the system from a Live CD or did you install from a live CD?

That card you mention is a broadcom, which do give trouble under Linux (I know that from hard experience I have one broadcom in this laptop)

You are probably going to need to install ndiswrapper to get it to work (that includes having handy the XP drivers of the card)

These links pertain to your card so they should give you some light about your current problem.

[http://wiki.linuxquestions.org/wiki/Broadcom_4318_Airforce_one_54g_card](http://wiki.linuxquestions.org/wiki/Broadcom_4318_Airforce_one_54g_card)
[http://ubuntuforums.org/showthread.php?t=482555](http://ubuntuforums.org/showthread.php?t=482555)

---

### Post by Nehvrook on 2007-10-10
Thanks for the reply. We're using 7.04 and it's installed to the hard drive. We used a live CD to install it.

I've checked out those links. I'll need to hunt down the correct drivers and give ndiswrapper a go. I'll report back on how it goes.

---

