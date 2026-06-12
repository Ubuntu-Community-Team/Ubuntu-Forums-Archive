---
title: "Please help me connect to the internet"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by whitey_1 on 2009-12-10
Hello everyone,

I have installed Ubuntu 9.10 on my desktop computer, it connects to the internet and works well. I have also installed Ubuntu 9.10 on my laptop but i cannot connect to the internet on it. On the desktop it detected the internet and i just needed to enter my wep key, worked fine. On the laptop though, it does not see the internet at all with Ubuntu, but it does work on the internet under windows vista.

I have a talktalk broadband account, there is a small box with an aereal on it. It is wireless internet.

When i was installing Ubuntu on the laptop i selected an option to say that i wanted to encrypt my files. I had not selected to say i wanted to encrypt my files when i installed Ubuntu on my desktop computer though.

On both installations the auto detection for the DHCP failed, so i choose the option to correct it later. Would this be the root of the problem?

Another thing i have noticed is that when i have been trying to set up Ubuntu on my laptop, the internet slows down alot on the desktop computer if i am doing both things together.

If anyone can offer any suggestions or questions, please help.

Thank you very much

---

### Post by sandyd on 2009-12-10
> **whitey_1 said:**
> Hello everyone,

I have installed Ubuntu 9.10 on my desktop computer, it connects to the internet and works well. I have also installed Ubuntu 9.10 on my laptop but i cannot connect to the internet on it. On the desktop it detected the internet and i just needed to enter my wep key, worked fine. On the laptop though, it does not see the internet at all with Ubuntu, but it does work on the internet under windows vista.

I have a talktalk broadband account, there is a small box with an aereal on it. It is wireless internet.

When i was installing Ubuntu on the laptop i selected an option to say that i wanted to encrypt my files. I had not selected to say i wanted to encrypt my files when i installed Ubuntu on my desktop computer though.

On both installations the auto detection for the DHCP failed, so i choose the option to correct it later. Would this be the root of the problem?

Another thing i have noticed is that when i have been trying to set up Ubuntu on my laptop, the internet slows down alot on the desktop computer if i am doing both things together.

If anyone can offer any suggestions or questions, please help.

Thank you very much
whats your laptop's wireless card?

---

### Post by FullDeck72 on 2009-12-10
im curiouse about this post as well, i am new to linux and im loveing every minute of it. however, the wireless card in my computer is now inactive with ubuntu and the wireless manager program in the downloadables is not sufficient.:(

---

### Post by whitey_1 on 2009-12-10
> **carlee said:**
> whats your laptop's wireless card?

Hello, 

Thanks for the reply.

The laptops wireless card is;
Broadcom 802.11b/g WLAN

---

### Post by Iowan on 2009-12-10
Do you have a model number? 
**lshw -C network** (from a terminal) *might* be able to help.

---

### Post by Iowan on 2009-12-10
Do you have a model number? 
**lshw -C network** (from a terminal) *might* be able to help.

---

### Post by whitey_1 on 2009-12-11
> **Iowan said:**
> Do you have a model number? 
**lshw -C network** (from a terminal) *might* be able to help.


I typed into the terminal **lshw -C network** , it returned the following;

  	 	 	 	 	 	  john@ubuntujohn:~$ lshw -C network  
 WARNING: you should run this program as super-user.  
   *-network                
        description: Network controller  
        product: BCM4311 802.11b/g WLAN  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:06:00.0  
        version: 01  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list  
        configuration: driver=b43-pci-bridge latency=0  
        resources: irq:18 memory:40000000-40003fff  
   *-network  
        description: Ethernet interface  
        product: RTL-8139/8139C/8139C+  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 8  
        bus info: pci@0000:08:08.0  
        logical name: eth0  
        version: 10  
        serial: 00:1b:38:3c:34:8a  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical  
        configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 multicast=yes  
        resources: irq:16 ioport:2000(size=256) memory:d0100000-d01000ff  
   *-network DISABLED  
        description: Wireless interface  
        physical id: 2  
        logical name: wlan0  
        serial: 00:1a:73:91:d4:ac  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 



Im hoping this will help. Please excuse the time it took for me to reply, ive just got home.


Thanks

---

### Post by bkratz on 2009-12-11
See this thread it may help

[http://ubuntuforums.org/showthread.php?t=1334754](http://ubuntuforums.org/showthread.php?t=1334754)

---

### Post by whitey_1 on 2009-12-11
> **bkratz said:**
> See this thread it may help

[http://ubuntuforums.org/showthread.php?t=1334754](http://ubuntuforums.org/showthread.php?t=1334754)

Hello,

I went to System/Administration/Hardware Drivers, after a short while it reported back that there are '   	 	 	 	 	  No proprietary drivers are in use on this system '


Do i need to install the 'windows wireless drivers - Ndiswrapper driver installation tool' ?


I cant download it on the laptop of course, because i cant get on the internet on the laptop. But i can get on the internet on my desktop computer, so can i download the software and put it on the laptop via a usb flash drive?


If so, what exact file am i looking for? is it the ' 0.8.4-1 (ndisgtk) ' ?


Please help,


Thank you

---

### Post by mcdjork on 2009-12-11
If you didn't install these driver during the live cd install, it isn't copied to your drive, and you need to get it off of the install CD. 

Put your Install CD into the drive, then go to System > Administration > Software Sources. Check the box about installable from the CDROM. Then open System > Administration > Synaptic Package Manager, search Broadcom, and install bcmwl-kernel-source and bcmwl-modaliases. Then open System > Admin > Harware Drivers. The STA driver should show up, install it. Restart, and it should work fine. 

You could also choose to install the b43-fwcutter, but I've had problems getting that connected to a Dynamic WEP network.

You COULD also, as you said, download these to your desktop's disk, copy the drivers over onto your laptop, but the way I described is better.

---

### Post by woodnymph on 2009-12-11
also check [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)
it worked for me.  there is a section to the bottom for No Alternate Internet Access

---

### Post by whitey_1 on 2009-12-11
> **mcdjork said:**
> If you didn't install these driver during the live cd install, it isn't copied to your drive, and you need to get it off of the install CD. 

Put your Install CD into the drive, then go to System > Administration > Software Sources. Check the box about installable from the CDROM. Then open System > Administration > Synaptic Package Manager, search Broadcom, and install bcmwl-kernel-source and bcmwl-modaliases. Then open System > Admin > Harware Drivers. The STA driver should show up, install it. Restart, and it should work fine. 

You could also choose to install the b43-fwcutter, but I've had problems getting that connected to a Dynamic WEP network.

You COULD also, as you said, download these to your desktop's disk, copy the drivers over onto your laptop, but the way I described is better.


Thank you for your answer, that has solved the issue!

Thanks to everyone else that has answered my question, brilliant.

---

