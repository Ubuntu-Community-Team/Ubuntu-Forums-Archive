---
title: "Unable to use network hardware"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Pauho on 2008-12-19
I've been unable to use either my Wi-Fi or Ethernet network hardware for the past month on my Ubuntu 8.10 install. My Wi-Fi is an Atheros AR5005G and the Ethernet is an Nvidia nForce.

Having typed "sudo lshw -C network" into the Terminal, I got this response:

 *-network UNCLAIMED     
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:04:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=80 maxlatency=28 mingnt=10
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0a:ee:13:e7:95:fe
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

So my Wi-Fi is UNCLAIMED and my Ethernet is DISABLED. I don't have a clue as to how this happened, never mind how to fix it. 

I've looked in the Ubuntu help (Wireless troubleshooting section) and it says to try using ndisgtk with a Windows *.inf driver. Now, I can't use Synaptic to get the package and I can only find an Atheros driver with a *.sys extension.

If someone could point out what to do or why I'm being stupid, I'd be very grateful. 

Paul

---

### Post by mikeyphi on 2008-12-20
Welcome!

Something to try - may work!

Your 'Disabled' ethernet: Right click on the 'network' icon in the top panel then click to enable Networking......if this is already enabled come back to us.

The wireless might be fixable (but you need an Internet connection first!!) by following the instructions here:  
[https://help.ubuntu.com/community/EeePC/Fixes](https://help.ubuntu.com/community/EeePC/Fixes)

from the section : Installing ath5k driver on Ubuntu 8.10 Intrepid Ibex

---

### Post by Pauho on 2008-12-20
Thanks for replying!

The "Enable Networking" box is already ticked. 

Also, tried looking for a .deb for the package mentioned in the EeePC guide (linux-backports-modules-intrepid-generic), but I'm unsure which is the most up to date version. Is this a good route to be trying?

cheers

---

### Post by wwusnobrdr on 2008-12-20
Yes, this is what you want to do.  The backports-generic package will always select the best version for your kernel.  You should be able to find this in synaptic.  If it still does not work after installing those and rebooting let me know.

---

### Post by mikeyphi on 2008-12-20
1. Check to make sure Ethernet is enabled in BIOS.

2. If you can't get Internet access to your system - you will have to use another Ubuntu system to download the software onto a CD and then onto your pc.

If you can't fix your wired ethernet - ask again about installing packages without Internet access. AptonCD (apt on CD) is one possibility.

---

### Post by Pauho on 2008-12-22
Ok, I'm come up against an embarrassing road-block. I tried installing the linux-backports-modules-intrepid-generic deb package (from [here]("http://packages.ubuntu.com/intrepid/linux-backports-modules-intrepid-generic").

Ubuntu won't let me install this, saying that I have another software manager open (the only thing I have open is the deb installer, no synaptic or anything like that). 

I've checks the system moniter and the managers suggested by the error message (synaptic, apt etc) are not open. 

Any ideas as to how I should proceed?

---

### Post by mikeyphi on 2008-12-23
A packet manager might be open (but not working) if it failed to install something.
Open a terminal and enter:

sudo dpkg --configure -a


Hopefully that will fix the open package manager, then you can try to install the software.

---

### Post by Pauho on 2008-12-23
Ah-ha! Fantastic, that worked! didn't need to install the deb after all. I entered the command you gave me, restarted and my wi-fi connected automatically. 

Thank you all for your help.

---

