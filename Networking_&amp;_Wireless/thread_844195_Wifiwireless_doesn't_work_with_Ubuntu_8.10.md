---
title: "Wifi/wireless doesn't work with Ubuntu 8.10"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by FS92 on 2008-06-29
Hello:)

I've just installed Ubuntu 8.10 on my Fujitsu Siemens ESPRIMO mobile v5515. I can't seem to connect to any wireless network. I can get get connected to internet, just not wireless, I have to use a network cable. A friend of mine has got the same problem. I can't even search for networks, it's just like it doesn't support wifi. I have both windows and Ubuntu on my laptop, I haven't got any problem with the wifi on windows. What do I have to do?
Thanks for all comments and help. :)

---

### Post by Pjotr123 on 2008-06-29
Try this:
[http://ubuntutip.googlepages.com/nointernetconnection](http://ubuntutip.googlepages.com/nointernetconnection)

---

### Post by ptsubin on 2009-01-17
I had a previous installation of ubuntu 8.04 in which i had installed firmwares using b43-fwcutter. From /lib/firmware i copied b43 and b43 legacy folders to the newly installed 8.10 /lib/firmwares and i restarted the system i saw wifi LED on and i am connected now. It looked simpler. Well I am usind dell Inspiron 1525

---

### Post by brotell on 2009-01-19
I am having the same problem I have dual booted with xp and ubuntu 8.10. My wireless internet with a bigpond blue toaster maxon model bp3-ext works with my xp but no joy with ubuntu. I cannot use an ethernet connection due to the wireless setup. Can anyone offer any suggestions.
Ta Terry

---

### Post by superprash2003 on 2009-01-19
go to the terminal and post output of the following commands
1)iwconfig
2)lshw -C network

---

### Post by brotell on 2009-01-20
The only access my computer has to my net connection is via a USB connection if i was using windows i use the disk supplied with toaster does this mean i will have to find a program that is compatable with ubuntu. I tried the inputs  you stated into terminal but no success.

Terry

---

### Post by superprash2003 on 2009-01-22
you need to post the output of that command..

---

### Post by fbunker on 2009-11-19
I hate this part... I have tried all sorts of drivers, but to no avail. This is what I got.

frank@frank-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

frank@frank-laptop:~$ lshw-C network
bash: lshw-C: command not found
frank@frank-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:98:39:37
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.2 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ce:2f:50:1e:09:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
frank@frank-laptop:~$ 




What am I doing wrong?

---

### Post by virgoptrex on 2010-01-07
> **fbunker said:**
> I hate this part... I have tried all sorts of drivers, but to no avail. This is what I got.

frank@frank-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

frank@frank-laptop:~$ lshw-C network
bash: lshw-C: command not found
frank@frank-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:98:39:37
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.2 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ce:2f:50:1e:09:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
frank@frank-laptop:~$ 




What am I doing wrong?
I am having same problem. I tried few links but none seem to work
Did you try the following?

 [http://onlyubuntu.blogspot.com/2009/07/howto-install-and-enable-broadcom.html](http://onlyubuntu.blogspot.com/2009/07/howto-install-and-enable-broadcom.html)

 I tried the following but didn't help me out

[http://tenthblog.com/ubuntu/ubuntu-how-to-enable-your-wireless-card-dell-broadcom-bcm4311/](http://tenthblog.com/ubuntu/ubuntu-how-to-enable-your-wireless-card-dell-broadcom-bcm4311/)

---

### Post by bkratz on 2010-01-07
> **virgoptrex said:**
> I am having same problem. I tried few links but none seem to work
Did you try the following?

 [http://onlyubuntu.blogspot.com/2009/07/howto-install-and-enable-broadcom.html](http://onlyubuntu.blogspot.com/2009/07/howto-install-and-enable-broadcom.html)

 I tried the following but didn't help me out

[http://tenthblog.com/ubuntu/ubuntu-how-to-enable-your-wireless-card-dell-broadcom-bcm4311/](http://tenthblog.com/ubuntu/ubuntu-how-to-enable-your-wireless-card-dell-broadcom-bcm4311/)

The quote you are referencing is for Atheros type drivers, is yours a Broadcom?
If so you should see this 

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

