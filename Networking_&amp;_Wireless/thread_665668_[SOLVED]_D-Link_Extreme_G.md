---
title: "[SOLVED] D-Link Extreme G"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by tad1073 on 2008-01-12
i installed a new wireless card on my desktop today. Ubuntu is the only OS on the system but it will not boot, booting from livecd. At start up i checked bios at it detected the wifi card(other network controllerr) it looks like i need a drver huh. Is it possible to get the driver w/o an internet connection? I also need help with where to put ndisgtk so the .inf file will be on the OS as well as the livecd.  

ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82557/8/9 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 08
       serial: 00:50:8b:9a:ab:3a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
 
*-network UNCLAIMED
       description: Network controller
       product: AR5416 802.11a/b/g/n Wireless PCI Adapter
       vendor: Atheros Communications, Inc.
       physical id: 3
       bus info: pci@0000:00:03.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=64
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


Installed ndisgtk installed net5416.inf, returned invalid driver Help!!!

---

### Post by tad1073 on 2008-01-13
Sombody help please... where do I put the .sys file no one seems to know, I have searched the forums and no ons has any answers.

---

### Post by tad1073 on 2008-01-13
someone, anyone...

---

### Post by amingv on 2008-01-14
Have you tried using ndiswrapper? I suggest the last version in [sourceforge]("http://sourceforge.net/project/showfiles.php?group_id=93482"). But you may try your luck with the one in the repos.

When you have it, cd to the directory where the windows drivers (basically a .inf and a .sys file) are and then:

```
sudo modprobe -r ndiswrapper
ndiswrapper -i <drivername>.inf
ndiswrapper -l 
[COLOR="Blue"]#you should get some output like this:
#bcmwl5: driver installed
#device (14E4:4320) present[/COLOR]
sudo modprobe ndiswrapper
```

Notice you provide the .inf file, NOT the .sys.

---

### Post by RomeReactor on 2008-01-14
Hi. Please open a terminal and run:
```
ndiswrapper -l
```
and:
```
lspci
```
And post the output of both.

---

### Post by tad1073 on 2008-01-14
```
thomas@thomas-desktop:~$ ndiswrapper -l
net5416 : invalid driver!
thomas@thomas-desktop:~$ lspci
00:00.0 Host bridge: Broadcom CNB20LE Host Bridge (rev 05)
00:00.1 Host bridge: Broadcom CNB20LE Host Bridge (rev 05)
00:01.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
00:03.0 Network controller: Atheros Communications, Inc. AR5416 802.11a/b/g/n Wireless PCI Adapter (rev 01)
00:0f.0 ISA bridge: Broadcom OSB4 South Bridge (rev 4f)
00:0f.1 IDE interface: Broadcom OSB4 IDE Controller
01:04.0 SCSI storage controller: LSI Logic / Symbios Logic 53c895a (rev 01)
01:05.0 Ethernet controller: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 08)
01:06.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
01:07.0 System peripheral: Compaq Computer Corporation Advanced System Management Controller
05:01.0 RAID bus controller: Digital Equipment Corporation DECchip 21554 (rev 01)

```

---

### Post by tad1073 on 2008-01-14
```
thomas@thomas-desktop:~$ ndiswrapper -i net5416.inf
driver net5416 is already installed
thomas@thomas-desktop:~$ ndiswrapper -l
net5416 : invalid driver!

```

---

### Post by RomeReactor on 2008-01-14
You need to remove the module and uninstall the driver:
```
sudo modprobe -r net5416
```
and:
```
sudo ndiswrapper -r net5416
```
I'm not familiar with your card, but [here]("http://ubuntuforums.org/showthread.php?t=512828&highlight=AR5416") is a how-to that may help. [This post]("http://ubuntuforums.org/showthread.php?p=3884923&highlight=AR5416#post3884923") in particular might be of interest to you.

---

### Post by tad1073 on 2008-01-14
thanks for the help

---

