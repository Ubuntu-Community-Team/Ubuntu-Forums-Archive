---
title: "Wireless Woes"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by Shyper on 2007-07-06
Hey, I'm a total newb to Linux and Ubuntu. I just finished installation, and right now, I'm trying to establish by Internet connection. My only Internet/network connection is a Westell 802.11g USB Wireless Adapter; this connects to a Westell router. I have no idea on how to get it working in Linux. Is there any way I can use my adapter as-is, or do I have to buy another adapter? Thanks.

---

### Post by fredj on 2007-07-06
Which version of ubuntu are you using, is it Feisty?
What is your computer. Can you open a terminal and enter this command
sudo lshw -class network
Then post the result here.

---

### Post by Shyper on 2007-07-06
It's the latest version of Ubuntu, 7.04. I guess that would be Feisty.

 *-network               
       description: Ethernet interface
       product: 82562V 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:69:7a:f4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI firmware=1.1-2 latency=0 multicast=yes
       resources: iomemory:dfde0000-dfdfffff iomemory:dfddb000-dfddbfff ioport:ecc0-ecdf irq:17

This is with the USB adapter plugged in, btw.

---

### Post by Shyper on 2007-07-06
Well, I looked around and installed ndiswrapper, then used it to wrap my Westell USB Adapter's drivers. The whole installation/wrapping procedure seems to have gone fine (I followed the ndiswrapper's wiki's documentation to the letter), but my adapter still doesn't work - it refuses to light up or work at all. Can anyone help? Thanks.

---

### Post by fredj on 2007-07-07
How did you install your version of ndsiwrapper. The version that is in the Feisty standard repositories
doesn't seem to work. I have wasted a lot of time with it. The only way to get a good version seems to
be to download the latest source files from the ndiswrapper website and compile them.

Open a terminal window. Type ndiswrapper -v and post the message that you get here.

What sort of access point are you trying to connect to? Does it have encryption? If so is it WEP or
WPA encryption?

---

### Post by ugm6hr on 2007-07-07
There is no mention of support for a Westell USB adapter in the ndiswrapper wiki.

It may be a rebranded version of another manufacturer's device.  If you post the results of ```
lsusb
``` you can search the wiki for it.  Is there another name for it?

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

---

