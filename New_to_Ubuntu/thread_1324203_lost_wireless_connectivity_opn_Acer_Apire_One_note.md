---
title: "lost wireless connectivity opn Acer Apire One notebook"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by Alexandre76 on 2009-11-12
Hi,

I was connected fine, when I suddenly lost the wireless network. I tried to restart network services and also to reboot, but the only connection i can get is with Ethernet.

If this can help :
```
julie@julie-laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for julie: 
 * Reconfiguring network interfaces...                                                                                       Ignoring unknown interface eth0=eth0.

``` 
```

julie@julie-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```
lshw give this :

```
      *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:23:8b:29:28:50
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.13 latency=0 multicast=yes
                resources: irq:27 ioport:2000(size=256) memory:51010000-51010fff(prefetchable) memory:51000000-5100ffff(prefetchable) memory:51020000-5103ffff(prefetchable)

```

No sign of Wireless adapter here :(

Alex

Thanks in advance for your help

---

### Post by ukripper on 2009-11-12
post output of:
```
iwconfig
```

check network button on your netbook is turned on. Can you see the wifi light?

---

### Post by Alexandre76 on 2009-11-12
> **ukripper said:**
> post output of:
```
iwconfig
```

check network button on your netbook is turned on. Can you see the wifi light?

The wifi light is on, and if I touch the switch it stays on... output of iwconfig is already in my first post :)

Thanks for your response anyway

---

### Post by ukripper on 2009-11-12
can you post output of:
```
lsmod
```

---

### Post by Alexandre76 on 2009-11-13
> **ukripper said:**
> can you post output of:
```
lsmod
```

I tried to apply the following guide, and it didn't work. 

[http://ubuntuforums.org/showthread.php?t=1305812&highlight=atheros+ar5bxb63](http://ubuntuforums.org/showthread.php?t=1305812&highlight=atheros+ar5bxb63)

I will reinstall 9.04 which was working fine, because this small notebook is not mine and the owner (my 8 years old cousin) wants it back asap :) there had been some huge changes in the 9.10 version with which I only have problems.

I have another laptop Packard Bell MZ35-200 on which 9.10 wouldn't run at all, just 9.04

---

### Post by ukripper on 2009-11-13
> **Alexandre76 said:**
> 

I have another laptop Packard Bell MZ35-200 on which 9.10 wouldn't run at all, just 9.04

Are you getting any error messages on taht laptop with  9.10?

---

### Post by Alexandre76 on 2009-11-13
> **ukripper said:**
> Are you getting any error messages on taht laptop with  9.10?

The Packard Bell laptop was running fine with 9.04, I wanted to run the upgrade which completed successfully. But impossible to boot it. Tried to make a fresh install on it, i eventually managed after several attempts to complete the install, but could never boot it. Installed 9.04, no problems.

---

### Post by ukripper on 2009-11-13
> **Alexandre76 said:**
> The Packard Bell laptop was running fine with 9.04, I wanted to run the upgrade which completed successfully. But impossible to boot it. Tried to make a fresh install on it, i eventually managed after several attempts to complete the install, but could never boot it. Installed 9.04, no problems.

could be live cd problem. Check the cd before you install. i never come across installtion problem with ubuntu ever. Installed 9.10 on 10+ machines for my clients now.

---

### Post by Alexandre76 on 2009-11-13
> **ukripper said:**
> could be live cd problem. Check the cd before you install. i never come across installtion problem with ubuntu ever. Installed 9.10 on 10+ machines for my clients now.

I did that already, the same live cd was used for installing on the Netbook from Acer, didn't have any problems. I am sure there is an issue with that model and 9.10. I also tried from a CD rom and a USB drive... same result, 9.10 won't boot.

---

### Post by ukripper on 2009-11-13
What kind of installion problem you are having with 9.10 on that laptop? Does it give you any error during boot?

---

### Post by 3rdalbum on 2009-11-13
Shut down fully, and then boot up again.

---

### Post by Alexandre76 on 2009-11-13
> **ukripper said:**
> What kind of installion problem you are having with 9.10 on that laptop? Does it give you any error during boot?

I didn't see any error messages. The setupo would just freeze at some point. I tried several times using various installation medium (CD, USB drive...), eventually succeded, but won't boot at all, while 9.04 (using the same USB drive reformated with 9.04) installed and ran smoothly.

---

### Post by ukripper on 2009-11-13
Did you try to bootup with 9.10 live cd/usb. Or you just ran installion setup only?

---

### Post by lucy_t on 2009-11-30
This isn't one of the most intelligent solutions and is a bit sledgehammer but I have used wicd to solve wireless problems before and my wifes acer one (that I am now working on wireless with wpa) lost it's connection, prompting for the wireless password, and then lost the ability to enable wireless in network mamanger.

after reading I just:

sudo apt-get install wicd

(you may need the right repo's)

and it removed the bundled network mgr and on starting wicd it all worked....

worth a go.

---

