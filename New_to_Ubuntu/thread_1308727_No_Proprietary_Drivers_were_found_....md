---
title: "No Proprietary Drivers were found ..."
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Doug0 on 2009-10-31
OK, this might be the same old story as everyone else's, but I'm not sure.

Just installed 9.10 on a Dell Inspiron 5300 desktop.  
9.04 had worked fine, but I installed clean.

The Broadcom 43 driver appeared in the System|Admin|Drivers under the 9.10 LiveCD.
The I full installed and now I have no proprietary drivers.

In trying to get a BC43 installed, 'Ive:

installed bcmwl-kernel-source
installed b43-fwcutter a few times
run tar xfvj broadcom-wl-4.80.53.0.tar.bz2
used ndisgtk to install the bcmwl6 .inf and .sys from Windows

OK, what am I doing wrong that I never have a driver show?

---

### Post by pastalavista on 2009-10-31
> **Doug0 said:**
> OK, this might be the same old story as everyone else's, but I'm not sure.

Just installed 9.10 on a Dell Inspiron 5300 desktop.  
9.04 had worked fine, but I installed clean.

The Broadcom 43 driver appeared in the System|Admin|Drivers under the 9.10 LiveCD.
The I full installed and now I have no proprietary drivers.

In trying to get a BC43 installed, 'Ive:

installed bcmwl-kernel-source
installed b43-fwcutter a few times
run tar xfvj broadcom-wl-4.80.53.0.tar.bz2
used ndisgtk to install the bcmwl6 .inf and .sys from Windows

OK, what am I doing wrong that I never have a driver show?

I don't believe you need proprietary drivers any more. My Atheros drivers are included in the kernel. Have you checked network manager to see if wireless is enabled?

---

### Post by Doug0 on 2009-10-31
Yes, in fact I'm posting here using a USB dongle.
But my PCI card doesn't work.

---

### Post by pastalavista on 2009-10-31
Is Karmic recognizing the broadcom card? Post the outputs of ```
 lshw -C network && lspci
```

---

### Post by wojox on 2009-10-31
Try running System|Admin|Update Manager again and check System|Admin|Drivers

---

### Post by Doug0 on 2009-11-01
I ran update manager.

> **pastalavista said:**
> Is Karmic recognizing the broadcom card? Post the outputs of ```
 lshw -C network && lspci
```

Relevant results of lshw were:

```

 *-network UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=0
       resources: memory:fddfe000-fddfffff
...
02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

---

### Post by ikt on 2009-11-01
If you do this:

lspci -vnn | grep 14e4

does anything come up?

---

### Post by Doug0 on 2009-11-01
> **ikt said:**
> If you do this:

lspci -vnn | grep 14e4

does anything come up?

02:00.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

---

### Post by Nordicnurse on 2009-11-01
I've also been having problems with bcm4318 & 9.10.

> **Doug0 said:**
> 
In trying to get a BC43 installed, 'Ive:

...
run tar xfvj broadcom-wl-4.80.53.0.tar.bz2
...

I've been trying to google for solution and found this (haven't tried though): [http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new)

With Karmic, should you use broadcom-wl-4.150.10.5.tar.bz2 for firmware?

---

### Post by Xenomorph05 on 2009-11-01
I have a Broadcom 43 and my 9.10 didn't detect I needed drivers for it at first. 

My solution was just to run the update manager and then I started the System->Admin->Hardware Drivers and it rescanned my computer and it worked.

---

### Post by Doug0 on 2009-11-01
I tried the two suggests above to no avail.

When I boot the LiveCD, I can activate the driver and see the PCI in the Network Manage panel, but with a "device not ready" message.  Apparently this is due to some bug in the 9.10 kernel, per some other discussions.

For now, I'll just count myself lucky to have my USB dongle and wait for a patch.

---

### Post by Nordicnurse on 2009-11-01
> **Doug0 said:**
> I tried the two suggests above to no avail.

When I boot the LiveCD, I can activate the driver and see the PCI in the Network Manage panel, but with a "device not ready" message.  Apparently this is due to some bug in the 9.10 kernel, per some other discussions.

For now, I'll just count myself lucky to have my USB dongle and wait for a patch.

Just FYI, (writing this at work) if I remember correctly, I have the same wireless card on my laptop. It works just by selecting b43 from hardware drivers but is insanely slow. Trying to fix it, I tried bcmwl, which killed the whole connection. 
For my problem, i'll try wicd next if it helps.

as a second thought, refering to [http://ubuntuforums.org/showthread.php?t=1139412](http://ubuntuforums.org/showthread.php?t=1139412) and to reply #9 by Ayuthia..
while you tried to get b43 to work, did you try anything of this sort?
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```

---

### Post by spearofsolomon on 2009-11-06
This is a really goofy problem.  I assume that you are not connecting to the internet through the wired ethernet while you are trying to get your wireless card to work?

I think the problem (and I just had the same one) is that because you aren't connected to the net, ubuntu isn't seeing the drivers for your card (or anything else).  I went into administration->software sources, unchecked everything that was online, checked the CD as a source, unchecked all the update stuff as well, closed that, and rebooted.  I think you could also go to administration->update manager and do a "check" instead of rebooting.  Anyway next time I went to Hardware Drivers the wireless card showed up again because it is on the cd.  I installed the drivers and afterward I put everything back the way it was - you definitely want online sources and updates.  After you do that, you should be able to do another administration->update manager->check and open Hardware Drivers again and see if there are any other drivers (like nvidia) that you want to install from online sources.

The next problem you're probably going to have is that for some stupid reason, installing the wireless driver does not configure it to load at boot.  So the next time you reboot, your wireless won't work again until you do "modprobe wl".  If you edit /etc/modules (carefully) and add "wl" to the last line, your wireless will work at boot.

For the lazy, do  
```
echo wl | sudo tee -a /etc/modules
```in a terminal and then do 
```
cat /etc/modules
```to see if it worked.

> **Doug0 said:**
> OK, this might be the same old story as everyone else's, but I'm not sure.

Just installed 9.10 on a Dell Inspiron 5300 desktop.  
9.04 had worked fine, but I installed clean.

The Broadcom 43 driver appeared in the System|Admin|Drivers under the 9.10 LiveCD.
The I full installed and now I have no proprietary drivers.

In trying to get a BC43 installed, 'Ive:

installed bcmwl-kernel-source
installed b43-fwcutter a few times
run tar xfvj broadcom-wl-4.80.53.0.tar.bz2
used ndisgtk to install the bcmwl6 .inf and .sys from Windows

OK, what am I doing wrong that I never have a driver show?

---

