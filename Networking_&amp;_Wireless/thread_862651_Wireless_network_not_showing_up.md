---
title: "Wireless network not showing up?"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by buzz1170 on 2008-07-17
This is my first time using Ubuntu, my friend convinced me to try it.

When I click on the internet icon in the upper-right-hand corner, it doesn't show any wireless networks under "wireless networks."

I checked through the help files and I think Ubuntu doesn't recognize my wireless card. It's built into my laptop, so I don't know the name of the card (or anything else). My laptop is an Acer 4620Z. The switch doesn't say "on" or "off."

---

### Post by chili555 on 2008-07-17
Let's ask the computer what kind of card you have. Open a terminal and do:```
sudo lshw -C network
```Next, let's ask it if the switch is on or off:```
sudo cat /var/log/messages | grep switch
```Then we can try to get it going.

---

### Post by buzz1170 on 2008-07-17
This is what I get:

```
danieltobin@danieltobin-laptop:~$ sudo lshw -C network
[sudo] password for danieltobin: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:00:b2:4b
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.23 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:d9:2f:81:fc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
danieltobin@danieltobin-laptop:~$ sudo cat /var/log/messages | grep switch
Jul 17 20:09:59 danieltobin-laptop kernel: [   23.229352] SMP alternatives: switching to UP code
Jul 17 20:09:59 danieltobin-laptop kernel: [   23.797635] SMP alternatives: switching to SMP code
Jul 17 20:09:59 danieltobin-laptop kernel: [   24.064632] ACPI: EC: non-query interrupt received, switching to interrupt mode
danieltobin@danieltobin-laptop:~$ 
```

---

### Post by buzz1170 on 2008-07-17
I think it has something to do with the wireless hardware, because I can connect fine in Vista.

---

### Post by buzz1170 on 2008-07-17
> **chili555 said:**
> Let's ask the computer what kind of card you have. Open a terminal and do:```
sudo lshw -C network
```Next, let's ask it if the switch is on or off:```
sudo cat /var/log/messages | grep switch
```Then we can try to get it going.

BTW I used the WUBI installer, I don't know if that's a problem. Is there a way to install Ubuntu so I can choose whether to start Vista or Ubuntu b/c WUBI did that and I liked that.

---

### Post by buzz1170 on 2008-07-17
After looking around on Google, I found ndiswrapper and wondering what it does?

---

### Post by buzz1170 on 2008-07-17
Would downloading a driver work?
I have a Broadcom 802.11g Network Adapter. What should I download?

---

### Post by chili555 on 2008-07-17
I suggest you hook up the wired ethernet connection and do:```
sudo apt-get update
sudo apt-get install b43-fwcutter
```This will download and install the firmware needed by your wireless. It is not provided by default, since it's not open source. Then you should be able to enable your wireless card.

Post back if you get stuck.

---

### Post by kunixos on 2008-07-17
To answer your wireless question, you have a Broadcom Wireless card. You may be able to get it working with the standard Ubuntu Hardware Drivers Manager (just check the box next to Broadcom Wireless and it'll download/update your computer to work) or if that doesn't work you might have to do some ndiswrapper magic. Search the wiki or forum for ndiswrapper, broadcom or bcm43xx for more information, but the HDM should take care of it (I have an Acer Aspire 9410Z and it worked perfectly in Kubuntu).

As for installing Ubuntu so you can choose whether to start Vista or Ubuntu, this will be done in the installation if you do a fresh CD install (ie. put the cd in and reboot). However, it's important to understand that you will have to create disk space for Ubuntu and will probably resize/remove Vista (if you choose) so be aware of what you are selecting in the installation. Then, once you get to the 'boot' section (where it asks you to install a MBR and shows you other operating systems on your HDD) just make sure that Windows shows up. If not (and you're sure it's still there) then when you get your Ubuntu setup done, open a terminal and type
```
sudo fdisk -l
```
which will show you all of your partitions on all of your HDDs. Find your Windows partition and do a:
```
sudo gedit /boot/grub/menu.list
```
and then put at the bottom
```
title Windows Vista
rood (sd1,1)
chainloader +1
```
where sd1,1 means sdb2 (so if your Windows partition is on sda2 it would be sd0,1).

Hope this helps!

---

### Post by buzz1170 on 2008-07-17
> **chili555 said:**
> I suggest you hook up the wired ethernet connection and do:```
sudo apt-get update
sudo apt-get install b43-fwcutter
```This will download and install the firmware needed by your wireless. It is not provided by default, since it's not open source. Then you should be able to enable your wireless card.

Post back if you get stuck.

I did all that and it seems to have worked. I haven't unplugged the ethernet cable yet and tried the wireless. I'm letting Ubuntu install some updates. Once I'm done, all I have to do is unplug my ethernet and choose my wireless internet connection?

---

### Post by buzz1170 on 2008-07-17
> **kunixos said:**
> To answer your wireless question, you have a Broadcom Wireless card. You may be able to get it working with the standard Ubuntu Hardware Drivers Manager (just check the box next to Broadcom Wireless and it'll download/update your computer to work) or if that doesn't work you might have to do some ndiswrapper magic. Search the wiki or forum for ndiswrapper, broadcom or bcm43xx for more information, but the HDM should take care of it (I have an Acer Aspire 9410Z and it worked perfectly in Kubuntu).

As for installing Ubuntu so you can choose whether to start Vista or Ubuntu, this will be done in the installation if you do a fresh CD install (ie. put the cd in and reboot). However, it's important to understand that you will have to create disk space for Ubuntu and will probably resize/remove Vista (if you choose) so be aware of what you are selecting in the installation. Then, once you get to the 'boot' section (where it asks you to install a MBR and shows you other operating systems on your HDD) just make sure that Windows shows up. If not (and you're sure it's still there) then when you get your Ubuntu setup done, open a terminal and type
```
sudo fdisk -l
```
which will show you all of your partitions on all of your HDDs. Find your Windows partition and do a:
```
sudo gedit /boot/grub/menu.list
```
and then put at the bottom
```
title Windows Vista
rood (sd1,1)
chainloader +1
```
where sd1,1 means sdb2 (so if your Windows partition is on sda2 it would be sd0,1).

Hope this helps!

Not to sound like a moron, but where is the Ubuntu Hardware Drivers Manager? And thanks for the other tips on installing Ubuntu. :)

---

### Post by buzz1170 on 2008-07-17
> **chili555 said:**
> I suggest you hook up the wired ethernet connection and do:```
sudo apt-get update
sudo apt-get install b43-fwcutter
```This will download and install the firmware needed by your wireless. It is not provided by default, since it's not open source. Then you should be able to enable your wireless card.

Post back if you get stuck.

THANK YOU! It worked! I'm wireless!!! :KS

---

### Post by mackhina on 2008-07-30
Thanks so much! The code below submitted by chili555:KS worked a treat!  Before entering this into the terminal thingy my wireless card wasn't even powering.  My cards an old cnet CWC-800.

sudo apt-get update
sudo apt-get install b43-fwcutter

Once again, thanks for the useful advice.  Much appreciated.

Cheers

Mick

---

