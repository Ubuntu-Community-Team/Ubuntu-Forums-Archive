---
title: "Wifi usb dongle activation without wire connection"
date: 2014-11-06
forum: Networking &amp; Wireless
---

### Post by stepppin on 2014-11-06
I would like to activate a wifi USB device, TOTO Link "N150USM" on the latest stable version of ubuntu.
64 bit

I think I have installed the driver for Linux, provided in the TOTO website below, on the ubuntu.
[http://www.tamio.com.tw/tamio/component/phocadownload/category/62-totolink-n150usm?download=340:n150usm-rtl8188c-driver](http://www.tamio.com.tw/tamio/component/phocadownload/category/62-totolink-n150usm?download=340:n150usm-rtl8188c-driver)

I moved all the files downloaded to Home directory. 
Among the files downloaded there was a file with an extention ".sh", or "install.sh",
 and typed as follows in the terminal.

[COLOR=#333333][FONT=Verdana]$ chmod 755 install.sh[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]$ ./install.sh

[/FONT][/COLOR]The process was completed with success.


Now I can see the wifi mark above the screen without any signal.
Usb wifi device is sticked in a usb terminal.

When I click the wifi mark above, there appears no list of signals detected.

I typed some codes following instructions I found somewhere in a forum, where trouble shootings were explained.
Then the terminal answered "wire connected" even though no wire connection available currently.
I tried other codes to check sth that I do not know what they are, and the terminal responded with too much results to read and check them all.
So I could not make use of them.

I use some Windows PC and all of them getting signals from the same buffalo.


I cannot use wired connection to the Ubuntu.


Is there anything I can do now?

Thanks for your help in advance.

---

### Post by Bucky Ball on 2014-11-06
*Thread moved to **Networking & Wireless**.*

Welcome. Please open a terminal and paste this in:

```
sudo lshw -C network
```

Paste the results back here, please.

You should create a folder in /home and put the files in there, then navigate to that folder in a terminal rather than extracting and running the driver from your /home folder. Post the results of the command and let's see where you're up to.

---

### Post by stepppin on 2014-11-06
Hi Thank you for your reply. I will reply the result as soon as possible, hopfully within 12 hours.

(I remember I tried that code before and responded with "wii 81xx" or sth, but I will try it again.)

---

### Post by stepppin on 2014-11-09
The command gave me some information back.

PCI (sysfs)   
  *-network                
       description: Ethernet interface 
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       logical name: eth0 
       version: 0c 
       serial: 44:8a:5b:25:92:c6 
       size: 10Mbit/s 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s 
       resources: irq:91 ioport:e000(size=256) memory:fea00000-fea00fff memory:d0800000-d0803fff 

Regards

---

