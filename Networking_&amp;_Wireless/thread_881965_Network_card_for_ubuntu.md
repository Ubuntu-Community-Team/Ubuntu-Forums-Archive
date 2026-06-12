---
title: "Network card for ubuntu?"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by steve.knoblock on 2008-08-06
I built a system with an ASUS PQ5 motherboard. This has Atheros onboard LAN, which is not supported by most Linux distros. I had a Dlink DFE-530TX Plus card around, so I thought I could use it instead of the onboard network interface.

I could not burn a full install CD (it is 700K) on the CD's and burner I have available right now, so I burned a CD with minimal (network) install for Hardy. It booted okay, but could not find a network interface. I went back to the Ubuntu HCL and checked the chipset on my card against the list...mine is Realtek RTL8139A and the HCL where it says "works out of the box" is RTL-8139C.

Apparently, the difference between A and C is enough that it won't recognize it.

Is there some network interface card I can get that is certain to work with Ubuntu? Or some other way to get my Dlink card to work?

---

### Post by pytheas22 on 2008-08-06
It's very rare that an ethernet card won't work out-of-the-box, although perhaps the environment provided by the network install CD doesn't include all of the drivers that are on a normal system.

To better troubleshoot your problem, it would be useful to know the device ID of your NIC chipsets.  If you run the command:
```

lspci -nn
```

it will tell you. There are probably different versions of RTL-8139C and it would be helpful to know exactly which one you're dealing with.  With that information, we can do some research to see if there's a solution.

Another thing to check is that it's not just an issue with getting an IP.  If you run the command "ifconfig," do you see any network interfaces (eth0 or eth1) mentioned (anything besides 'lo')?  If so, then you probably just need to run a command like:
```

sudo dhclient eth0
```

to get connected.

You should not need to buy a new ethernet card to get online in Linux, so please don't do that unless we really decide that there's absolutely no better solution.

Finally, I'm wondering why you're unable to burn the Ubuntu CD in the first place.  It should work on any normal CD (I think that everything made these days has a capacity of at least 700 megabytes).  If you're burning the CD in Windows, are you sure that you're doing it correctly?  Windows doesn't know how to deal with ISO files properly, so you need to use a third-party tool, not XP's built-in CD burner.  I actually think it would be easier to figure out what's going on with the CDs than troubleshooting the network card.

---

### Post by steve.knoblock on 2008-08-06
> **pytheas22 said:**
> 
Finally, I'm wondering why you're unable to burn the Ubuntu CD in the first place.  It should work on any normal CD (I think that everything made these days has a capacity of at least 700 megabytes).  If you're burning the CD in Windows, are you sure that you're doing it correctly?  

Thanks for the suggestions on how to check out the nic. I'll try those.

I swapped my NEC DVD burner out to the new machine and that is the drive I usually go to for burning CDs or DVDs, so I can't burn a DVD at the moment. Right now, I have a LiteOn CD burner in this machine. I'm using Nero, and it gives the CD capacity as 657MB or 74min. Nero can burn an .iso image.

---

### Post by pytheas22 on 2008-08-06
> I'm using Nero, and it gives the CD capacity as 657MB or 74min. Nero can burn an .iso image.

That's strange.  Are you sure your CDs have a 700-megabyte capacity?  You might also want to try isorecorder, a [tiny and free ISO]("http://isorecorder.alexfeinman.com/isorecorder.htm") writer for Windows, to see if it works better than Nero.

---

### Post by steve.knoblock on 2008-08-06
The blank CDs have been around a while. I can believe Nero when it says they are 650MB capacity.

---

### Post by pytheas22 on 2008-08-06
> The blank CDs have been around a while. I can believe Nero when it says they are 650MB capacity.

In that case, I think your best option would be to buy 700 megabyte CDs (sorry if you already said that they were 650 megabyte; I guess I wasn't understanding correctly).  It should definitely work then.

Otherwise, if you still want to try to troubleshoot the network driver problem, we can do that, but I think a much easier solution would be just to get new disks and burn a full live CD.

---

### Post by steve.knoblock on 2008-08-06
I dropped into the shell from the installer. The D-Link interface is listed as 05:01.0 0200 D-Link RTL8139 [1186:130] (Rev 10).

When I entered ifconfig, it did not respond with anything. I looked around and found /bin/ethdetect and ran it. A setup screen listing ethernet drivers came up, there were two for the Realtek models (including C), one was 8139too RTL-8139. I assume this is somewhere over the network since it won't find it normally. Is there a way to put this on a USB drive and point setup to it?

---

### Post by pytheas22 on 2008-08-06
Yes, the two Realtek drivers are 8139too and 8139cp.  I think Ubuntu uses 8139too by default, but sometimes the other one is necessary for certain cards.

I don't think it would work to simply copy the drivers from somewhere else, because they'd need to be compiled against the same kernel that the installer is using.  Are you sure they're not already on the CD?  If the command:
```

locate 8139
```

returns anything, then they're there.  Or if you type:
```

sudo modprobe 8139too
sudo modprobe 8139cp
```

without getting any errors, then they must be on the CD.

---

