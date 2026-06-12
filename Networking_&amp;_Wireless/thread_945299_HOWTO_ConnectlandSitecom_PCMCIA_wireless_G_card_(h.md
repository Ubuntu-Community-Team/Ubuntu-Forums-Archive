---
title: "HOWTO: Connectland/Sitecom PCMCIA wireless G card (hardy)"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by chrisharte on 2008-10-12
Hi, I just managed to get a Connectland PCMCIA wireless card (model number 5510006 WIRE-CNL-G-PCM) to work after some digging around so maybe this information might be useful to others:

**Background**

lspci returns:

03:00.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

After searching this I found that this device is similar to the Sitecom WL-140 from this bug report: [[COLOR="Blue"]bug report 120978[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/120978")

The bug report says that the linux prism54 driver should already support it but there are timing issues (which should be fixed in Intrepid) that mean it fails to work out of the box on hardy. So, until then it is possible to download the windows driver for the WL-140 card from the sitecom website and use ndiswrapper.

**Instructions:**

If not installed already, install the packages ndiswrapper-common and ndiswrapper-utils-1.9:

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

Download the sitecom WL-140 V2 windows driver: [[COLOR="Blue"]Sitecom driver page[/COLOR]]("http://sitecom.com/drivers_result.php?groupid=5&productid=342&version=V2;001")

Extract WL-140v2.zip into a folder of your choice and cd to it.

Install the sitecom driver INF file with ndiswrapper
```
 sudo ndiswrapper -i WL54Cfg.INF
```

Check that it's there
```
sudo ndiswrapper -l 
```

It should say something like:

wl54cfg : driver installed
	device (1260:3890) present (alternate driver: p54pci)

start it up: 
```
sudo modprobe ndiswrapper
```

At this point, all going well the lights should start flashing on the card and the wireless should start to work...

Finally, to make the card work when you boot your system, run this command to create the appropriate ndiswrapper aliases:
```
sudo ndiswrapper -ma
```

Hope this is helpful to other people.

---

