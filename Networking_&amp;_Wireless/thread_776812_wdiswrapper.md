---
title: "wdiswrapper"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by blah569 on 2008-04-30
Okay, so I have added the drivers into the ndiswrapper gtk, but, I am still unable to connect to my wireless.  Here is a screenshot:  [http://bay01.imagebay.com/_upload/img/33/Screenshot-1.png](http://bay01.imagebay.com/_upload/img/33/Screenshot-1.png)  (I do not see the ability to connect to wireless in the network manager).

Anyway, I forgot the terminal command, it is something like wconfig, or such, but it displays two values, eth0, and another one I can not remember, as I was not paying too much attention.  Both of the values proclaimed "no wireless extensions."

So, does anyone have any other steps I can take?  If anyone is wondering, my wireless card is RTL8186B, but I thought (I received the drivers from a support technician), that the driver should still work.  Anyway, does anyone have any advice to help me?  Thanks.

---

### Post by preschooldropout on 2008-05-01
I'm having this same problem, it worked fine in gutsy gibbon until I upgraded.

---

### Post by agim on 2008-05-01
Here is the hardy fix that I used with ndiswrapper. Something about things loading in the right order.

Here are the directions:

Step 5 (run in terminal)

sudo gedit /etc/init.d/wirelessfix.sh

Step 6

Paste the followings in the opened file(wirelessfix.sh)and make sure you save it before continuing Step 7

#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

Step 7 (run in terminal)

Run this :

cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh

Step 8 (run in terminal)

finally run this:

sudo update-rc.d wirelessfix.sh defaults

Step 9

Restart your machine and enjoy the freedom from those wires....



obtained from here:
[http://ubuntuforums.org/showthread.php?t=766560&highlight=ndiswrapper+hardy](http://ubuntuforums.org/showthread.php?t=766560&highlight=ndiswrapper+hardy)

and also here, for a little more info:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by agim on 2008-05-01
*mis-post*

---

### Post by blah569 on 2008-05-01
> **agim said:**
> Here is the hardy fix that I used with ndiswrapper. Something about things loading in the right order.

Here are the directions:

Step 5 (run in terminal)

sudo gedit /etc/init.d/wirelessfix.sh

Step 6

Paste the followings in the opened file(wirelessfix.sh)and make sure you save it before continuing Step 7

#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

Step 7 (run in terminal)

Run this :

cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh

Step 8 (run in terminal)

finally run this:

sudo update-rc.d wirelessfix.sh defaults

Step 9

Restart your machine and enjoy the freedom from those wires....



obtained from here:
[http://ubuntuforums.org/showthread.php?t=766560&highlight=ndiswrapper+hardy](http://ubuntuforums.org/showthread.php?t=766560&highlight=ndiswrapper+hardy)

and also here, for a little more info:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
I have attempted what you have said, and I still see this in the connection options:  [http://bay01.imagebay.com/_upload/img/33/Screenshot-2.png](http://bay01.imagebay.com/_upload/img/33/Screenshot-2.png)

---

### Post by Ayuthia on 2008-05-01
Can you post your info from lshw -C network?

---

### Post by blah569 on 2008-05-01
> **Ayuthia said:**
> Can you post your info from lshw -C network?

```

Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)


```

That is what I see from the terminal function you told me to use.

---

### Post by bedfordd on 2008-05-01
Try

> lshw -C Network
or
> sudo lshw -C Network

---

### Post by Ayuthia on 2008-05-01
> **blah569 said:**
> ```

Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)


```

That is what I see from the terminal function you told me to use.

I am guessing that something was typed incorrectly.  I copied and pasted the command I posted and it listed fine.  It might have been possible that you left out a space between the C and network.  I received your result when I did it that way.

EDIT:
You can also try Bedfordd's post.  It will do the same thing.

---

### Post by blah569 on 2008-05-01
This is what I have:

**Edit 1:**
I just thought that I should mention that this is not my primary computing device, so if the "stats" do not look very great, this is not my primary laptop.


```

 *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:df:b5:88
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.12 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s


```

---

### Post by blah569 on 2008-05-01
I am sorry to double post, but I would really like some help.

---

### Post by Ayuthia on 2008-05-02
Well, the information you posted only showed your wired network...  Can you post your lspci -nn?  I just want to see if your wireless card is noticed.

---

