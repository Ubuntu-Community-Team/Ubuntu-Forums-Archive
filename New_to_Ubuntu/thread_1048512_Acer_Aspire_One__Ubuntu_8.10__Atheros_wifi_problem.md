---
title: "Acer Aspire One / Ubuntu 8.10 / Atheros wifi problem"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by jlott on 2009-01-23
i have just installed ubuntu 8.10 desktop edition on a acer aspire 1 netbook and i can't get the wireless to work

please help

from Joseph

---

### Post by jlott on 2009-01-23
I have just installed ubuntu 8.10 desktop edition and i can't get the wireless to work

please help

from Joseph

---

### Post by gettinoriginal on 2009-01-23
You can try this:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by bapoumba on 2009-01-23
Threads merged.

---

### Post by anewguy on 2009-01-23
Have you installed any driver for it yet in Ubuntu, or just trying get it to work for the first time?

Post the output of these terminal commands back here so we can go from there:

(in a terminal windows -> applicatons/accessories/terminal)

lspci

lshw -C network

The first command will list any hardware detected on the PCI buss.  If your wireless is built-in it probably will show in this list.

The second command will list any network hardware (if there is no driver for your wireless currently installed your wireless adapter may not show here).

Post those back and we can go from there.

dave :)

---

### Post by Michael.Godawski on 2009-01-23
hi,

have a look at this basic guide dealing with setting up wlan:


[LIST]
[*][http://ubunturesources.ub.ohost.de/solvingwireless.html](http://ubunturesources.ub.ohost.de/solvingwireless.html)
[/LIST]

---

### Post by nothingspecial on 2009-01-23
Go to system > administration > hardware drivers then disable anything in there.

Then

```
sudo apt-get install linux-backports-modules-intrepid-generic

```
To load the driver

```
sudo modprobe ath5k
```

To make it load everytime you boot


```
gksudo gedit /etc/modules

```
and add

```
ath5k
```
To the end of the file

save
close
reboot

---

### Post by jlott on 2009-01-24
I have a acer aspire one net book which I put ubuntu 8.10 on and I can't get the wireless to work

PLEASE HELP

From Joseph

---

### Post by anewguy on 2009-01-24
You never replied to my request for information in your previous post about this same problem.  Please do the following:

(1) Open a terminal windows (applications/accessories/terminal)

(2) Type:

lspci <press enter>  

This will list the PCI devices on your PC, which will hopefully include your wireless adapter.  This information is needed to know what type of wireless adapter it is and what type of driver and instructions to give you.  Please copy the entire output and paste back in a reply here.

(3) Type:

lshw -C network <press enter>

This will list your hardware, isolated down to network hardware by the "-C network" string.  This will tell us if your wireless adapter is seen and if it has a driver applied.  Post the output of the command also with the above information.


In the future, be sure to check your original thread and follow up on it.  There have been a few replies there, with no answer from you, so people probably assumed you either had it working or gave up.  Dual posts just add confusion.  If you want to bring your post back "up" in the list, just add a reply with "bump" in the text (actually, ANY text, just most use bump to indicate they are still looking for help).  Please do not bump more than 1 time in 24 hours.

If you provide the above information we may be able to help you.

dave :)

---

### Post by jimrz on 2009-01-24
> **jlott said:**
> I have a acer aspire one net book which I put ubuntu 8.10 on and I can't get the wireless to work

PLEASE HELP

From Joseph

It would help a great deal if you would post which wifi card / chipset the box has. If you are not sure, open a terminal and type
```
lspci
```

---

### Post by nothingspecial on 2009-01-24
Go to system > administration > hardware drivers then disable anything in there.

Then```


sudo apt-get install linux-backports-modules-intrepid-generic
```

To load the driver


```
sudo modprobe ath5k
```

To make it load everytime you boot

```
gksudo gedit /etc/modules
```

and add


```
ath5k
```

To the end of the file

save
close
reboot

---

### Post by jlott on 2009-01-24
(2)00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

type 3 
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:e4:8e:48
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.5 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1e:dd:0e:d0:08:84
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by nothingspecial on 2009-01-24
Hey wait a minute, I already did this. In a previous post by you. 

Now I don`t mind helping beginners because I was helped myself. But why are you asking the same question again? If my answer didn`t work then say so. There is another method for getting those pesky atheros drivers working, but try this simple one first. If it doesn`t work then say so. 

I`d rather not repeat myself.

---

### Post by jlott on 2009-01-24
i have not re posted the question?

it just puts the question to the top of the list when you quick reply

look at the message above the on from you. that is a reply I sent to someone (called dave) who contacted me to help before you did first did

---

### Post by nothingspecial on 2009-01-24
Ok did it not work

---

### Post by jlott on 2009-01-24
when it typed in sudo modprobe ath5k nothing happened

also when i typed in the next bit it came up with this

[B]# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp[/B]

**_[COLOR="Red"]go to next page[/COLOR]_**

---

### Post by nothingspecial on 2009-01-24
Ok, have you added the line to /etc/modules and rebooted? I`ll write youy a little how to if not.

---

### Post by jlott on 2009-01-24
it said command not found

---

### Post by nothingspecial on 2009-01-24
```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
```
```

tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
```

If you`ve not got the necessary compiling tools get them


```

sudo apt-get install build-essential linux-headers-$(uname -r)
```

Navigate to the madwifi directory

```
cd madwifi-hal-0.10.5.6*/
```

Compile

```
make
```
```

sudo make install
```

Load the driver

```
sudo modprobe ath_pci
```

Make it load every time


```
gksudo gedit /etc/modules
```

put a # in front of ath5k

Add this line to the end of the file

Code:

```
ath_pci
```

---

### Post by jlott on 2009-01-24
it says to _cd madwifi-hal-0.10.5.6*/_

joseph@Joseph-laptop:~$ cd madwifi-hal-0.10.5.6*/
bash: cd: madwifi-hal-0.10.5.6*/: No such file or directory

---

### Post by nothingspecial on 2009-01-24
Ok joe don`t worry. What is the name of the madwifi file you have?

---

### Post by eddielgarcia on 2009-01-24
I had the same problem.  I followed the aspire Ubuntu directions in the support pages to no avail using module auth_pci.  I used the other one in these directions rebooted and all worked great.  Looks like my hardware was different ath5k worked great for me!

 Re: Wireless is not working PLEASE HELP ME!!!!
Go to system > administration > hardware drivers then disable anything in there.

Then
Code:

sudo apt-get install linux-backports-modules-intrepid-generic

To load the driver


Code:

sudo modprobe ath5k

To make it load everytime you boot

Code:

gksudo gedit /etc/modules

and add


Code:

ath5k

To the end of the file

save
close
reboot

---

### Post by jlott on 2009-01-24
here is all th stuff you told me to type in

joseph@Joseph-laptop:~$ wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz)
--2009-01-24 23:18:38--  [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz)
Resolving snapshots.madwifi-project.org... 217.24.1.134
Connecting to snapshots.madwifi-project.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 45 [application/x-gzip]
Saving to: `madwifi-hal-0.10.5.6-current.tar.gz.2'

100%[======================================>] 45          --.-K/s   in 0s      

2009-01-24 23:18:49 (976 KB/s) - `madwifi-hal-0.10.5.6-current.tar.gz.2' saved [45/45]

joseph@Joseph-laptop:~$ tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
joseph@Joseph-laptop:~$ sudo apt-get install build-essential linux-headers-$(uname -r)
[sudo] password for joseph: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.27-9-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joseph@Joseph-laptop:~$ cd madwifi-hal-0.10.5.6*/
bash: cd: madwifi-hal-0.10.5.6*/: No such file or directory
joseph@Joseph-laptop:~$ cd madwifi-hal-0.10.5.6*/
bash: cd: madwifi-hal-0.10.5.6*/: No such file or directory
joseph@Joseph-laptop:~$ make
make: *** No targets specified and no makefile found. Stop.
joseph@Joseph-laptop:~$

---

### Post by jlott on 2009-01-24
The link you sent was blocked by pop up blocker, please re send (pop up blocker now off)

---

### Post by neu2buntu on 2009-01-24
[http://ubuntuforums.org/showthread.php?t=1012973](http://ubuntuforums.org/showthread.php?t=1012973)

heres how i got it working permanently,

---

### Post by shahin on 2009-01-24
I am not sure if I may ask a question on the same thread, if not, please let me know.  I do not even see my wireless card in the output of lspci.  What should I do please? 
:~# lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
06:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 01)

---

### Post by neu2buntu on 2009-01-24
there is no need to install this madwifi snapshot. as i said in my post above ,follow this link here [http://ubuntuforums.org/showthread.php?t=1012973](http://ubuntuforums.org/showthread.php?t=1012973) 

and you will have no more bother with wifi even after kernel updates

---

### Post by shahin on 2009-01-24
I am trying to unpack the file, but nothing happens.  Not even an error message:
#:~/wifi# tar -xvf madwifi-hal-0.10.5.6-current.tar.gz 
#~/wifi# ls
madwifi-hal-0.10.5.6-current.tar.gz
#~/wifi#

---

### Post by jujiro_eb on 2009-02-10
I am not sure if your problem is resolved.  But downgrading the kernel to 2.6.7-9 will fix both wired and wireless issues.

---

### Post by shahin on 2009-02-21
Thanks.  I was focusing on a different effort for a while.  I tried the card on a different pc, and used Fedora 10. Wireless came right up.  I am not sure how to downgrade to a different Kernel version.  Does it mean downgrading from 8.10 to 8.04, or can you just downgrade the kernel?  How is that done please?

---

### Post by neu2buntu on 2009-02-21
how can i get it through to you people on here,im on my acer aspire one now and after every kernel update my wifi still works running 8.10 just follow my post above(i know it drags on a bit because i forgot half the stuff)and you will be ok!!  i am going to do a how to on this step by step !!!!

---

