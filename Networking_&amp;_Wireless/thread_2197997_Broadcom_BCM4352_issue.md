---
title: "Broadcom BCM4352 issue"
date: 2014-01-06
forum: Networking &amp; Wireless
---

### Post by testing031199 on 2014-01-06
I recently installed ubuntu 12.04.3 LTS on my Asus G750 laptop. The wireless is not working. To be more specific, I need the correct drivers, and I do not know how or where to get them. I am a newbie when comes to these sorts of things, so please be patient. Also, some helpful information might be that...
1)
lspci | grep -i wireless
returns 
03:00.0 Network controller: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter (rev 03)
2)
uname -a
returns
Linux marc 3.8.0-35-generic #50~precise1-Ubuntu SMP Wed Dec 4 17:25:51 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
3)
I have installed bcmwl-kernel-source and that did nothing. It is still installed.
4)
When I open up Additional Drivers, there is no longer an option for the BCM STA drivers, even though the bcmwl-kernel-source is installed.
5)
Ubuntu is installed right next to windows 8.2.


I have been working on this for about a week now, and have looked at countless forums, so any help is greatly appriciated.
Also this is my first time posting, so any tips on layout are also appriciated.

Thanks

---

### Post by newagelink on 2014-01-06
You might try [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) . I hope you can resolve your issue by reading through and following this webpage. :)

---

### Post by Bucky Ball on 2014-01-06
Welcome. Please open a terminal and post the output of this command:

```
sudo lshw -C network
```

Thanks.

PS: For code, use [code] tags. You can add them manually or hit 'Adv Reply' for a new post, paste the code in, highlight it and click the '#' icon.

---

### Post by testing031199 on 2014-01-06
Thanks newagelink, but I have already been there and nothing has worked so far. 

Bucky ball:

```
 *-network               
       description: Network controller
       product: BCM4352 802.11ac Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:18 memory:dd400000-dd407fff memory:dd200000-dd3fffff
  *-network
       description: Ethernet interface
       product: QCA8171 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 10
       serial: ac:22:0b:b7:fd:2c
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx driverversion=1.2.3 duplex=full firmware=N/A ip=192.168.1.87 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:19 memory:dd500000-dd53ffff ioport:d000(size=128)
```

Thank you very much for responding so quickly.

---

### Post by Bucky Ball on 2014-01-06
Is this to say you were using the STA driver previously? The driver shown in your output (driver=wl) is the STA driver as far as I know.

(PS: I have put [code] tags around your code so you can see how it's done; neater, more compact, easier to read. ;))

---

### Post by testing031199 on 2014-01-06
The first time I booted, I opened Additional Drivers and clicked on the Broadband STA drivers. I got an error. I then installed the bcmwl-kernel-resouce, which I tested using modprobe, and it didnt work. So I wasnt using drivers. I just had them. Anyways, I am having some critical issues with apt-get, so I thing I am going to reinstall ubuntu 12.04.3. Thanks a lot, and  i will post the response to your earlier segment of code.

[FONT=arial]thanks again[/FONT]

---

### Post by testing031199 on 2014-01-06
Alright so I kindof fixed it the easy way. I replaced ubuntu 12.04.3 with 12.10 and it worked with no problem at all. Thank you for all the help, I appriciate it.

---

### Post by Cole_Laidlaw on 2014-02-16
I hate to be the newbie on this topic, but I have the same latptop, I'm running Windows 8.1 and have Linux Ubuntu 12.10 installed on a flash drive. I upgarded from 12.04 after reading this forum, but how did you actually get the driver to work for the wireless card? I'm using a usb wireless card for the meantime but would love to not need excess hardware on such a great machine. 

Step-by-step would be absolutley amazing if you could explain for the ill-informed. I am very new to Linux.

---

### Post by gi11i4m on 2014-12-29
> **Cole_Laidlaw said:**
> I hate to be the newbie on this topic, but I have the same latptop, I'm running Windows 8.1 and have Linux Ubuntu 12.10 installed on a flash drive. I upgarded from 12.04 after reading this forum, but how did you actually get the driver to work for the wireless card? I'm using a usb wireless card for the meantime but would love to not need excess hardware on such a great machine. 

Step-by-step would be absolutley amazing if you could explain for the ill-informed. I am very new to Linux.

If you still have the issue, have you tried just going to 'Additional Drivers' and selecting the driver for your card? You might have to be connected.

---

### Post by Bucky Ball on 2014-12-29
> **gi11i4m said:**
> If you still have the issue, have you tried just going to 'Additional Drivers' and selecting the driver for your card? You might have to be connected.

Welcome. This is a very old thread and it is also marked as solved (the solution was to install 12.10 which is no longer supported so redundant). Thanks for sharing your thoughts, though.

(BTW, yes, the OP did try Additional Drivers and it didn't help.)

*Thread closed. *

---

