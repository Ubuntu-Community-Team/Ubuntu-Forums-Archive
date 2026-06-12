---
title: "Ubuntu 8.04 issues"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by Gtone on 2008-12-27
Hi all!!!

I just installed ubuntu 8.04 on an Acer Aspire One and i have some issues

1) It will not recognize any usb device every time i insert a stick or a hard drive i get this message ''Invalid mountoption when attempting to mount the volume'' 
how can i ''change'' this option?

2) I have no WiFi Support. I heard somewere about a project called mad wifi witch i visited but i couldn't understand nothing (i'm almost a newbie) is there an easer way to get WiFi to work?

3) Is there a way to make the gdesklets icon invisible in the system tray when running? (Nothing wrong with it i just can't find a reason to be there)

Thnak you all for your time.

---

### Post by nhasian on 2008-12-27
1) not sure about #1 but you can see what devices are attached via usb with the command *lsusb*.

2) we need to see what wifi adaptor you have. in a terminal type:

```
lshw -C network
```

3) I havent used gdesklets but I can put the screenlets tool in the system tray.

---

### Post by Gtone on 2008-12-28
ok the output of lshw -C network was:

> gtone@Netbook:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:b6:1c:eb
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.5 latency=0 module=r8169 multicast=yes
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
gtone@Netbook:~$ 



I can also see that my computer is using 2 restricted drivers for wireless i supose witch are:

1. Atheros Hardware Access Layer (HAL)
2. Support for Atheros 802.11 Wireless LAN Cards

But still i can't find any wireless networks...I have to tell you that my computer has a switch for the wireless but it's not working...


Now for the usb problem, I put a usb stick on my computer and this is the output of lsusb after puting the stick

> gtone@Netbook:~$ lsusb
Bus 005 Device 004: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash 110 USB 2.0 Flash Drive (2GB)
Bus 005 Device 003: ID 064e:d101 Suyin Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c062 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
gtone@Netbook:~$ 


I have no idea what the code says...but i can see my logitech mouse on that list that is working properly but the jetflash is not working and i also saw now that it says it's a 2GB usb but it's a 4GB stick if that makes any difference....

Please help me to keep ubuntu on the AAO i love them!!!

Have a Happy New Year Everyone

---

### Post by Gtone on 2008-12-28
Looking through the forum i found some other commands that the output might help someone to fix my problem here they are:

**iwconfig**

> gtone@Netbook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

gtone@Netbook:~$ 

**ifconfig**

> gtone@Netbook:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:b6:1c:eb  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:feb6:1ceb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3148 errors:0 dropped:3201475832 overruns:0 frame:0
          TX packets:2424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3927470 (3.7 MB)  TX bytes:250104 (244.2 KB)
          Interrupt:219 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1014 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1014 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50700 (49.5 KB)  TX bytes:50700 (49.5 KB)

gtone@Netbook:~$ 

**sudo iwlist scan**

> gtone@Netbook:~$ sudo iwlist scan
[sudo] password for gtone: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

gtone@Netbook:~$ 


hope this can give enough info about my computer...:(

---

### Post by Tom--d on 2008-12-28
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

Look there.

---

### Post by Gtone on 2008-12-28
i tryed that link and followed the instructions for installing madwifi theese are the commands that i used:

> wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz)
sudo apt-get install build-essential linux-headers-$(uname -r)
mkdir madwifi-hal-current
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz -c madwifi-hal-current
cd madwifi-hal-current
make
make install
modprobe ath_pci

and this was the output of the terminal:

> gtone@Netbook:~$ wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz)
--16:24:23--  [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz)
           => `madwifi-hal-0.10.5.6-current.tar.gz'
Resolving snapshots.madwifi-project.org... 217.24.1.134
Connecting to snapshots.madwifi-project.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,421,132 (4.2M) [application/x-gzip]

100%[===================================>] 4,421,132    495.96K/s    ETA 00:00

16:24:35 (381.68 KB/s) - `madwifi-hal-0.10.5.6-current.tar.gz' saved [4421132/4421132]

gtone@Netbook:~$ sudo apt-get install build-essential linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.24-22-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  mcpp linux-headers-2.6.24-19-generic libglib1.2ldbl ndiswrapper-common
  gnome-bin libgtk1.2 libgnome32 gnome-libs-data libatk1-ruby1.8 libart2
  libgnorbagtk0 ruby1.8 libgif4 libgnomeui32 libglib2-ruby1.8
  libcairo-ruby1.8 libgdk-pixbuf2-ruby1.8 libgtk1.2-common imlib-base
  liborbit0 gdk-imlib11 libgtk2-ruby1.8 libgnomesupport0 libzvt2 libruby1.8
  linux-headers-2.6.24-19 libpango1-ruby1.8 libgnorba27
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gtone@Netbook:~$ mkdir madwifi-hal-current
gtone@Netbook:~$ tar -xzf madwifi-hal-0.10.5.6-current.tar.gz -c madwifi-hal-current
tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.
gtone@Netbook:~$ cd madwifi-hal-current
gtone@Netbook:~/madwifi-hal-current$ make
make: *** No targets specified and no makefile found.  Stop.
gtone@Netbook:~/madwifi-hal-current$ make install
make: *** No rule to make target `install'.  Stop.
gtone@Netbook:~/madwifi-hal-current$ modprobe ath_pci

it seems that it can't make it through the last steps but have no idea what is going wrong...:(

---

### Post by BDNiner on 2008-12-28
It seems like when you tried to extract the archive it failed. Can you verify that you have a directory named madwifi-hal-current and there are files in that directory. make cannot find the makefile that should be contained in madwifi-hal-current.

If there is a directory and it contains all the extracted files then I would try and download the archive again and re-extract it. I find it easier to use nautilus to extract an archive by right-clicking on the archive and selecting extract here, unless you don't have a GUI at the moment.

---

### Post by unutbu on 2008-12-28
Try 

```
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6*/
make
make install
modprobe ath_pci

```

(the guide had a typo.) When you execute the tar command, the extracted directory is called madwifi-hal-0.10.5.6-r3879-20081204.
That's quite a mouthful.

---

### Post by pastalavista on 2008-12-28
you might try-- ```
sudo aptitude install madwifi-tools
```if you don't have the repository, you can download it [here]("http://packages.ubuntu.com/intrepid/madwifi-tools")

---

### Post by Gtone on 2008-12-28
ok i installed madwifi tools fine but now i can't find them?

The other instalation of madwifi with the typo didn't work for the same reasons...

---

### Post by pastalavista on 2008-12-28
> **Gtone said:**
> ok i installed madwifi tools fine but now i can't find them?

The other instalation of madwifi with the typo didn't work for the same reasons...

Just realized the madwifi-tools won't work unless you can install madwifi. I think it may be included in the Intrepid (8.10) kernel. You can still get it as a .deb package by adding repositories from [this page]("http://packages.ubuntu.com/intrepid/madwifi-tools"). Deb packages have made my life much simpler. I don't enjoy "programming" so much where one little typo can cause such frustration. Good-luck.

sorry... meant this page
[http://madwifi-project.org/wiki/UserDocs/Distro/Debian/MadWifi](http://madwifi-project.org/wiki/UserDocs/Distro/Debian/MadWifi)

---

### Post by kansasnoob on 2008-12-28
> **Gtone said:**
> Hi all!!!

I just installed ubuntu 8.04 on an Acer Aspire One and i have some issues

1) It will not recognize any usb device every time i insert a stick or a hard drive i get this message ''Invalid mountoption when attempting to mount the volume'' 
how can i ''change'' this option?

2) I have no WiFi Support. I heard somewere about a project called mad wifi witch i visited but i couldn't understand nothing (i'm almost a newbie) is there an easer way to get WiFi to work?

3) Is there a way to make the gdesklets icon invisible in the system tray when running? (Nothing wrong with it i just can't find a reason to be there)

Thnak you all for your time.

(1) Install pmount from synaptic or from terminal:

```
sudo apt-get install pmount
```

Brief description: > mount removable devices as normal user
pmount is a wrapper around the standard mount program which permits normal
users to mount removable devices without a matching /etc/fstab entry. This
provides a robust basis for automounting frameworks like GNOME's Utopia
project and confines the amount of code that runs as root to a minimum.

This package also contains a wrapper "pmount-hal" which reads some
information like device labels and mount options from hal and passes
them to pmount. Install the package "hal" if you want to use this
feature.

If a LUKS capable cryptsetup package is installed, pmount is able to
transparently mount encrypted volumes.


(2) I don't know much about wifi but have you looked at the Stickies here:

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

(3) The only thing I can think of is to right click an open space on either panel and click on Properties, then tick Autohide.

---

### Post by Gtone on 2008-12-28
pmount didn't work and neither usbmount that i found in the synaptic pacage manager...i'm starting to feel disapointed...:(

---

### Post by Gtone on 2008-12-28
ok partialy happy cause i solved the problem with the usb mounting i followed this guide 
[http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=164&start=10](http://www.aspireoneuser.com/forum/viewtopic.php?f=28&t=164&start=10)

now i have to see what i'm going to do with the WiFi...any new sugestions?

---

