---
title: "Broadcom WL Driver"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by dudude on 2008-06-10
I have a Dell 1720 laptop with a Broadcom 4310 Rev 1 wireless card 
I successfully got the card to work using ndiswrapper, but after I got an update to the linux-restricted-modules-2.6.24-18-generic package, the restricted driver manager shows that a new "wl" driver can be installed.

I haven't done much with the driver, since ndiswrapper was working.

I just wanted to see if anyone knows anything about this driver, and/or why it appears after this update.

---

### Post by Ayuthia on 2008-06-10
> **dudude said:**
> I have a Dell 1720 laptop with a Broadcom 4310 Rev 1 wireless card 
I successfully got the card to work using ndiswrapper, but after I got an update to the linux-restricted-modules-2.6.24-18-generic package, the restricted driver manager shows that a new "wl" driver can be installed.

I haven't done much with the driver, since ndiswrapper was working.

I just wanted to see if anyone knows anything about this driver, and/or why it appears after this update.
I was only able to find information about this in this [link]("https://launchpad.net/ubuntu/hardy/+source/linux-restricted-modules-2.6.24/2.6.24.13-17.38"):
  * Add new Broadcom driver that supports only PCI ID 14e4:4315. There is no
    overlap with any kernel driver, therefore no possiblity of regression.
If you type lspci -nn in the Terminal, you should see that this is your card.  However, I have not heard any confirmation on whether it works or if any additional configuration is needed.

---

### Post by Ayuthia on 2008-06-11
It looks like Broadcom released a driver for the 14e4:4315 card.  It is specifically for this card.  Like you already know, it is the wl module.  It is to be used instead of the b43 driver.  What this means is that you would have to blacklist the b43 driver.  You might have to add the wl module to /etc/modules so that it loads up at boot.

Here is the README.txt file from the Broadcom site:
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

Since the module is in linux-restricted-modules, I would not follow the instructions on how to install it.  I would just do the blacklisting of b43 and add wl to /etc/modules.  You might also want to verify that ieee80211_crypt_tkip is loaded also (lsmod|grep ieee80211_crypt_tkip).

---

### Post by punkrockguy318 on 2008-09-20
> **Ayuthia said:**
> It looks like Broadcom released a driver for the 14e4:4315 card.  It is specifically for this card.  Like you already know, it is the wl module.  It is to be used instead of the b43 driver.  What this means is that you would have to blacklist the b43 driver.  You might have to add the wl module to /etc/modules so that it loads up at boot.

Here is the README.txt file from the Broadcom site:
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

Since the module is in linux-restricted-modules, I would not follow the instructions on how to install it.  I would just do the blacklisting of b43 and add wl to /etc/modules.  You might also want to verify that ieee80211_crypt_tkip is loaded also (lsmod|grep ieee80211_crypt_tkip).

Should a bug be filed in Ubuntu?  Even with the restricted drivers manager, it requires you to disable the wl driver and enable it again for it to work properly.  Only with the quoted workaround can you get the wl driver to load everytime, even after you accept to use it in restricted drivers manager

---

### Post by Ayuthia on 2008-09-21
> **punkrockguy318 said:**
> Should a bug be filed in Ubuntu?  Even with the restricted drivers manager, it requires you to disable the wl driver and enable it again for it to work properly.  Only with the quoted workaround can you get the wl driver to load everytime, even after you accept to use it in restricted drivers manager

You might check and see if it is already posted as a bug, if it has not, you should create one.  The driver should be able to load automatically instead of having to do a workaround.

You might also check and make sure that the following modules are not loaded when you start up: b43, b43legacy, bcm43xx, ssb (unless you have a Broadcom wired ethernet connection), and ndiswrapper.  The way to check this is by doing the following:
```
lsmod|grep -i -e b43 -e bcm43xx -e ssb -e ndiswrapper
```
You don't need to add b43legacy because it will be grabbed by the b43 search.  It should not return anything unless you have a Broadcom wired ethernet connection that uses the b44 driver.  To see if you have this, do the following in the Terminal:
```
lshw -C network
```
It will return the information for your network cards.  At the bottom of the information for each card, it will tell you what driver the card is using.  If your wired card shows a b44 driver, you will then need to have ssb.  I have to say that I have not seen any 4315 cards that have a b44 wired card.

---

### Post by 3togo on 2008-09-26
Goto System->Administration->Hardware Drivers
1) Disable B43 and Enable Wl 
2) Reboot

To the least, it works for me.

---

### Post by e-square12 on 2009-08-10
*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:23:4e:d6:29:cf
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11

It seems my computer is using the wl driver and the b43 drivers are blacklisted. My wireless is still not working. Any suggestions? Thanks.

---

### Post by kngharv on 2009-10-27
Dear all:

This is more of a "linux" question than a "Broadcom wl" question, please bear with me.

the revision my Broadcom 4312, 14e4:4315, is only "partially" supported and kept giving me DMA error, so I am forced to use the official Broadcom driver.

I have follow the instruction compiled, and installed.  In my case, wl driver worked (after a long struggle cleaning up ndiswrapper and b43 driver settings, etc).

My issue is this.  My driver doesn't get loaded automatically.   Everytime I reboot, I need to go to the appropriate directory (/lib/modules/`uname -r`/kernel/driver/net/wireless... something like that)  and perform the following command line:

sudo insmod wl.ko


Once I done that, the driver will work like a charm.

My question to you all is, how to do so in a way that I don't have to do that everytime I reboot?

I tried "modprobe wl,"  but they can't find "wl."  the system can only find "wl.ko" if I am in that /lib/modules/.../kernel/driver/net/wireless directory.

do I need to copy wl.o to somewhere?  right now, I left it at where I compiled in the /var/tmp directory because i have no idea where to put it.  is it true that if I put "wl.o" file in somewhere appropriate, i can edit /etc/modules file and add "wl?"   Right now, it will say wl not found.


thanks in advance



Harvey

---

### Post by Ayuthia on 2009-10-27
> **kngharv said:**
> Dear all:

This is more of a "linux" question than a "Broadcom wl" question, please bear with me.

the revision my Broadcom 4312, 14e4:4315, is only "partially" supported and kept giving me DMA error, so I am forced to use the official Broadcom driver.

I have follow the instruction compiled, and installed.  In my case, wl driver worked (after a long struggle cleaning up ndiswrapper and b43 driver settings, etc).

My issue is this.  My driver doesn't get loaded automatically.   Everytime I reboot, I need to go to the appropriate directory (/lib/modules/`uname -r`/kernel/driver/net/wireless... something like that)  and perform the following command line:

sudo insmod wl.ko


Once I done that, the driver will work like a charm.

My question to you all is, how to do so in a way that I don't have to do that everytime I reboot?

I tried "modprobe wl,"  but they can't find "wl."  the system can only find "wl.ko" if I am in that /lib/modules/.../kernel/driver/net/wireless directory.

do I need to copy wl.o to somewhere?  right now, I left it at where I compiled in the /var/tmp directory because i have no idea where to put it.  is it true that if I put "wl.o" file in somewhere appropriate, i can edit /etc/modules file and add "wl?"   Right now, it will say wl not found.


thanks in advance



Harvey

You will need to have wl in /etc/modules.  It sounds like you are missing the module update:
```
sudo depmod -a
```
This will udpate the module dependencies and rebuild the module list so that modprobe can find it.

Hope that helps.

---

### Post by northd_tech on 2009-10-27
There are more threads on the Broadcom WiFi chipsets (including a link to Broadcom's source code to build a kernel module "wl.ko") at:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Wireless not working unless Broadcom STA driver is deactivated reactivated
[http://ubuntuforums.org/showthread.php?t=1049761](http://ubuntuforums.org/showthread.php?t=1049761)

"The driver is activated but not currently in use"
[http://ubuntuforums.org/showthread.php?t=1302412](http://ubuntuforums.org/showthread.php?t=1302412)

HOWTO: Use b43 driver with 14e4:4315 (Broadcom bcm4312 rev 01)
[http://ubuntuforums.org/showthread.php?t=1266620&page=8](http://ubuntuforums.org/showthread.php?t=1266620&page=8)

---

### Post by kngharv on 2009-11-01
> **Ayuthia said:**
> You will need to have wl in /etc/modules.  It sounds like you are missing the module update:
```
sudo depmod -a
```
This will udpate the module dependencies and rebuild the module list so that modprobe can find it.

Hope that helps.

THANKS!!!!  that
```
sudo depmod -a
```

worked!!! thanks


It works very well now, though i do wish I can have listening mode available :)

---

### Post by Ayuthia on 2009-11-01
> **kngharv said:**
> THANKS!!!!  that
```
sudo depmod -a
```

worked!!! thanks


It works very well now, though i do wish I can have listening mode available :)

Lucid Lynx might have that capability.  The b43 developers have done some work for the 4315 chipset so some of the cards with that chipset are starting to work with the b43 driver (it is introduced in the 2.6.32 kernel).

---

### Post by Oliver90001 on 2011-03-10
I've really been through the mill with this driver , I've got bcm4321.

I want o use b43 non-proprietary, open source driver, but this doesn't work its just non active no interface no error reported, and wl driver on ubuntu repositories is much the same !!!

However download the sta driver from Broadcom site:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
I had some hybrid driver, build this just ./configure & make ,don't make install.
Copy the wl.ko to /lib/modules/`uname -r`/kernel/drivers/net/wireless and delete and other instances of wl.ko 
depmod
modprobe -r ssb b43 wl
modprobe wl

*£%"$..... WORKS yipee

Now does anyone out there know how to actually make b43 work especially on bcm4321 as I can patch b43 and/or mac80211 (which it depends on) , and make the elusive 'Monitor' mode work. As you know .... its pointless sniffing a network, when your being noisy. My opinion is broadcom has done something quite low-level in response to the existence of a open-source driver to disable it, THATS ....JUST ...NOT ...Fair,
I've bought it now its mine, what happened to backward compatibility](*,):arrow:[-X

---

