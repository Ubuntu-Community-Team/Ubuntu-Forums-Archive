---
title: "Problems with Sony Vaio CW series"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by ralankford on 2010-06-21
I recently installed the newest Ubuntu distro on my Sony Vaio CW, and I'm having a few problems with it functioning right now.  It has apparently installed correctly, as I am using it to post this right now, but the screen on my laptop is black.  Everything seems to work whenever I plug this laptop via VGA into my TV.  I've read a few posts that claim to have solved the problem, but the instructions given there are a bit over my head.

I'm also having problems with slow internet connection speeds.  I am connected to my home network, but can't get any download speeds over 100 kbps and it is usually a lot slower than that.  I can't even download updates for Ubuntu through the update manager.  I've already disabled IPv6, and that seemed to help a little bit, but it is still about 20 times slower than the speeds I was getting while still using Windows 7.

Thanks for any help.

---

### Post by friv_livs on 2010-06-21
Please post the output of the following in terminal:

```
lshw -C network
```

---

### Post by ralankford on 2010-06-22
Here are the results
 *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 2c:81:58:f0:b3:1f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.2.3 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:e7a00000-e7a0ffff
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: 00:24:be:b8:db:8f
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:35 memory:e5220000-e5223fff ioport:a000(size=256) memory:e5200000-e521ffff(prefetchable)

---

### Post by friv_livs on 2010-06-22
Did you see this thread for your graphics issue?

[HTML]http://ubuntuforums.org/showthread.php?p=9215827[/HTML]

Also see if you can resolve the issue by trying a different nvidia driver from admin->synaptic.

For your wireless, try this thread:

[HTML]http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1341618&[/HTML]

You can use synaptic to get the packages recommended.

Hope this helps.

---

### Post by ref_de_leyendas on 2010-06-22
to solve the black screen of your laptop, you can follow the steps published in [http://ubuntuforums.org/showthread.php?t=1369420&highlight=nvidia+310m+sony+vaio+CW](http://ubuntuforums.org/showthread.php?t=1369420&highlight=nvidia+310m+sony+vaio+CW)
in my case, with kubuntu 9.10, to update the nvidia drivers had these problems.
now, following these steps have been resolved ...

edid file downloads of the post and the xorg configure as follows:

i did it like this- go to /etc/X11 and replace the xorg.conf file with the downloaded file from Simpsoni28 and also copy the sonycw.bin into the same folder.

1. If you cant replace the file open a terminal and write cd /etc/X11
2. then nano xorg.conf.
3. last part of the file should look like this:
Section "Device" 
Identifier	"Default Device" 
Driver	"nvidia" 
Option	"NoLogo"	"True" 
Option "ConnectedMonitor"	"DFP-0,DFP-1,CRT" 
Option	"CustomEDID"	 "DFP-0:/etc/X11/sonycw.bin" 
EndSection


4. close down nano with CTRL+X and save the file you changed.
5. it can be a good idea to activate the command for restarting x-server.
go to system-settings-keyboard-layouts-options.... and look for the the command to kill the x-server with ctrl+altbackspace.


Now I have solved the screen but I need to configure the output to my TV via HDMI.

I hope help you.
bye

---

### Post by sanju_bd on 2010-06-29
> **ref_de_leyendas said:**
> to solve the black screen of your laptop, you can follow the steps published in [http://ubuntuforums.org/showthread.php?t=1369420&highlight=nvidia+310m+sony+vaio+CW](http://ubuntuforums.org/showthread.php?t=1369420&highlight=nvidia+310m+sony+vaio+CW)
in my case, with kubuntu 9.10, to update the nvidia drivers had these problems.
now, following these steps have been resolved ...

edid file downloads of the post and the xorg configure as follows:

i did it like this- go to /etc/X11 and replace the xorg.conf file with the downloaded file from Simpsoni28 and also copy the sonycw.bin into the same folder.

1. If you cant replace the file open a terminal and write cd /etc/X11
2. then nano xorg.conf.
3. last part of the file should look like this:
Section "Device" 
Identifier    "Default Device" 
Driver    "nvidia" 
Option    "NoLogo"    "True" 
Option "ConnectedMonitor"    "DFP-0,DFP-1,CRT" 
Option    "CustomEDID"     "DFP-0:/etc/X11/sonycw.bin" 
EndSection


4. close down nano with CTRL+X and save the file you changed.
5. it can be a good idea to activate the command for restarting x-server.
go to system-settings-keyboard-layouts-options.... and look for the the command to kill the x-server with ctrl+altbackspace.


Now I have solved the screen but I need to configure the output to my TV via HDMI.

I hope help you.
bye

HI ref_de_leyendas,

did you figure out how to configure the HDMI output on your vaio? Would you mind posting the steps you followed? I am trying to configure the same thing with my LG 42 inch TV.

THanks

---

### Post by soulcheck on 2010-09-06
I stumbled upon this thread while looking for solutions to the slow wifi problem.

In case anyone else has that problem, it looks like installing dated compat-wireless from 03/09/2010 (dd/mm/yyyy ;)) solves it at least partially (Ï didn't notice any problems yet).

After six months of pain i finally get my max connections speed (12mb/s) in a room quite far away from router.

So get this file [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-09-03.tar.bz2]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-09-03.tar.bz2") or later, compile , install and have fun!

---

### Post by Scoup on 2010-09-26
> **soulcheck said:**
> I stumbled upon this thread while looking for solutions to the slow wifi problem.

In case anyone else has that problem, it looks like installing dated compat-wireless from 03/09/2010 (dd/mm/yyyy ;)) solves it at least partially (Ï didn't notice any problems yet).

After six months of pain i finally get my max connections speed (12mb/s) in a room quite far away from router.

So get this file [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-09-03.tar.bz2]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-09-03.tar.bz2") or later, compile , install and have fun!

How can I do that? My wireless is very slow and your answer is the only one that I found in internet.
Thanks

---

### Post by mathia on 2010-09-27
Please post the output of the following in terminal:

 	Code:
 	sudo lspci

---

### Post by Scoup on 2010-09-27
> **mathia said:**
> Please post the output of the following in terminal:

 	Code:
 	sudo lspci


```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
03:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

---

### Post by mathia on 2010-09-27
Hi,
I saw you have a 4380 network device from Marvell. This is the 88E8057 Gigabit ethernet  device.  You can dowload the vendor driver from here and give it a try to solve your slow internet connection:

[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "88E8057 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices	Linux 2.6 - Fedora v10.85.9.3

 $ sudo bash ./install.sh

and let me know if it works.

have a lot of fun ...:razz:

---

### Post by mathia on 2010-09-29
Hi,

are you still there? I am waiting for your results.

---

### Post by ref_de_leyendas on 2010-10-12
> **sanju_bd said:**
> HI ref_de_leyendas,

did you figure out how to configure the HDMI output on your vaio? Would you mind posting the steps you followed? I am trying to configure the same thing with my LG 42 inch TV.

THanks

The HDMI started working out with the latest version of the driver (256). . . The only drawback is that it recognizes, you need to log with the HDMI connected

(Sorry for my bad use of English)

---

