---
title: "No network connections"
date: 2016-06-28
forum: Networking &amp; Wireless
---

### Post by danny65 on 2016-06-28
Hi,
I have been using Ubuntu 12.04 on a live memory stick on an old laptop for a couple of days and had everything working apart from wireless, so I decided to install it as a clean install on the computer.
It got all the way thru the install and now I have no network adaptor showing for wired or wireless. I have tried a clean install with 16.04 with the same result. I cant get my head round how I can have it working when I boot from USB but not after an install to HDD.
I am guessing the info below may help a little


```
cooper@Inspiron-1501:~$ lspci -nn00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD/ATI] RS480/RS482/RS485 Host Bridge [1002:5950] (rev 10)
....
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:01.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)


cooper@Inspiron-1501:~$ sudo lshw -C network
[sudo] password for cooper: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:c0300000-c0301fff
cooper@Inspiron-1501:~$ 

```
oh and ifconfig only shows the local loopback 127.0.0.1 info.
Its a real pain to copy and paste from laptop to here via usb...

I have tried manually downloading and installing b43-fwcutter and the firmware-b43-install packages as mentioned in several other posts but I cant install them as the install button is greyed out on the package manager app.  Hope this makes some sense to you as I haven't gotten my 'hands dirty' with computers for a long long time.

Going to try 14.04.4 see if I have the same problems.

---

### Post by danny65 on 2016-06-28
OK. Installed 14.04.4 same problems, however I could install the firmware-b43-install package that I had on memory stick, but to no avail.
I will try some more tomorrow, Its frustrating that I have a wired connection when booting from a live usb but I dont after installing it. The wired link is dropped and reconnects during the install process mind you.
Oh and just in case it helps its a Dell Inspiron 1501 laptop.
My head hurts...

---

### Post by jeremy31 on 2016-06-28
The Network UNCLAIMED from your first post would tell me that you likely installed the Broadcom proprietary driver for wireless, to uninstall
```
sudo apt-get remove bcmwl-kernel-source broadcom-sta-common broadcom-sta-dkms
```

Reboot and see if the wired works so that you can ```
sudo apt-get install firmware-b43-installer
```

If wired still doesn't work after reboot use ```
grep [[:alnum:]] /etc/modprobe.d/* | grep b44
``` to see if the b44 module for wired connection is blacklisted somewhere else

---

### Post by danny65 on 2016-06-29
Thanks Jeremy, I now have a wired connection.

sudo apt-get install firmware-b43-installer gave me this
```
danny@Inspiron-1501:~$ sudo apt-get install firmware-b43-installer
[sudo] password for danny: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version.
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove it.
0 to upgrade, 0 to newly install, 0 to remove and 150 not to upgrade.
danny@Inspiron-1501:~$ 

```
Which looks to me like it was already there.

One step closer anyway, thanks

---

### Post by jeremy31 on 2016-06-29
Run the wireless script, see the link in my signature, and post the results from the wireless-info.**txt** file

---

### Post by danny65 on 2016-06-29
I have downloaded and run the script, here's the output attached.

On this laptop you have to use Fn+f2 to enable wifi, but this doesn't seem to do anything any more. The other Fn+ key combo's do work, for battery life, volume etc.
Wifi is enabled in BIOS as is the Fn key control to toggle it on and off. I have tried with the key control disabled with no luck.

---

### Post by jeremy31 on 2016-06-29
Something happened to the firmware, we can try
```
sudo apt-get purge firmware-b43-installer && sudo apt-get install firmware-b43-installer
```
Reboot

---

### Post by praseodym on 2016-06-29
Or install this package:
```

wget https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz  
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot.

---

### Post by danny65 on 2016-06-30
I will try these later, thanks guys, I found an old USB wifi stick that worked out of the box, so I have some sort of wifi now.
Thanks for your help so far....
I now need to take the laptop apart to give it a clean and probably replace the thermal paste as its idling at 70 degrees and hits 95+ if I try to do anything cpu intensive with it.

---

