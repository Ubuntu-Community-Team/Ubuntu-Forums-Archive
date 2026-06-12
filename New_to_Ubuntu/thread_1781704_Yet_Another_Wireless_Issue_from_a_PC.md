---
title: "Yet Another Wireless Issue from a PC"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by Miss_Spider on 2011-06-13
Good evening, all,

I've just installed wubi to play with Linux before I make a new-computer decision, and I can't manage to get the wireless to work. I'm working on a Dell Vostro 1510 and I'm fairly certain I have a Broadcom card, but I wouldn't swear to it.  Can anyone lead me through this?

Thanks,
Miss Spider

---

### Post by cariboo on 2011-06-13
Could you paste the output of lspci in you next post. If you don't have a working network connection, you can pipe the output of the lspci command to a text file using the following command:

```
lspci > lspci.txt
```

a text file called lspci.txt will br created in your home directory, you can then move the file by whatever means you have available to a system with a network connection.

The reason why I ask this, is that are several different broadcom drivers, it depends on which model you in order to recommend the correct driver

---

### Post by Miss_Spider on 2011-06-14
charlotte@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)


It does appear that the wireless connection is trying to get through.  The wireless symbol is showing up as blinking up and down, and it's trying to access the wireless of neighbors' houses as well.

---

### Post by Mynxenoa on 2011-06-14
```

charlotte@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

```

```
Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```

This is the name of your wireless card. You have the 4312 card. 

Here is a link to help you activate the card: 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43%20drivers)

PS - I have had a similar problem with trying to get the wireless card to work but it worked after I read all these steps. I made a thread about it. Now  I have an issue with trying to get the wireless to work on my partitioned OS.

---

### Post by Miss_Spider on 2011-06-14
Thanks for the link.  I tried to install, and got a strange error message back.  Let me post the transcript.  Do you see anything funky?  I honestly have no idea what's wrong.


charlotte@ubuntu:~$ sudo apt-get install b43-fwcutter
[sudo] password for charlotte: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.5 kB of archives.
After this operation, 81.9 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main b43-fwcutter amd64 1:013-3 [15.5 kB]
Fetched 15.5 kB in 0s (33.6 kB/s)       
Selecting previously deselected package b43-fwcutter.
(Reading database ... 132066 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a013-3_amd64.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-3) ...
charlotte@ubuntu:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following NEW packages will be installed:
  firmware-b43-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,632 B of archives.
After this operation, 49.2 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/multiverse firmware-b43-installer all 4.150.10.5-5 [3,632 B]
Fetched 3,632 B in 0s (9,215 B/s)           
Selecting previously deselected package firmware-b43-installer.
(Reading database ... 132073 files and directories currently installed.)
Unpacking firmware-b43-installer (from .../firmware-b43-installer_4.150.10.5-5_all.deb) ...
Setting up firmware-b43-installer (4.150.10.5-5) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Terl on 2011-06-14
Use System settings/Additional Drivers.  It will offer the Linux Sta driver.  Activate that and all will work well.  I have 2 Dells with the same broadcom card

---

### Post by Miss_Spider on 2011-06-14
I see Broadcom STA wireless driver, which is apparently already enabled.  Still no wireless.  I tried disabling it, thinking I could reinstall it, but I get a message about installArchives() failed.

Any thoughts?

---

### Post by Mynxenoa on 2011-06-17
> **Miss_Spider said:**
> Thanks for the link.  I tried to install, and got a strange error message back.  Let me post the transcript.  Do you see anything funky?  I honestly have no idea what's wrong.


charlotte@ubuntu:~$ sudo apt-get install b43-fwcutter
[sudo] password for charlotte: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.5 kB of archives.
After this operation, 81.9 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/main b43-fwcutter amd64 1:013-3 [15.5 kB]
Fetched 15.5 kB in 0s (33.6 kB/s)       
Selecting previously deselected package b43-fwcutter.
(Reading database ... 132066 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a013-3_amd64.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-3) ...
charlotte@ubuntu:~$ sudo apt-get install b43-fwcutter firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following NEW packages will be installed:
  firmware-b43-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,632 B of archives.
After this operation, 49.2 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/multiverse firmware-b43-installer all 4.150.10.5-5 [3,632 B]
Fetched 3,632 B in 0s (9,215 B/s)           
Selecting previously deselected package firmware-b43-installer.
(Reading database ... 132073 files and directories currently installed.)
Unpacking firmware-b43-installer (from .../firmware-b43-installer_4.150.10.5-5_all.deb) ...
Setting up firmware-b43-installer (4.150.10.5-5) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)

I want to say its some sort of bug, I say you look in the additional drivers after trying the commands once again. You should report it as well. I believe you should remove both of them. (can be found in the synaptic package manager) The STA driver in the additional drivers does not work with my computer which is a personal note. Make sure you reset the box after you insert those commands.

---

### Post by Mynxenoa on 2011-06-17
You could also use ndiswrapper, and grab the windows os drivers for the broadcom card.

---

