---
title: "networking problem with ubuntu"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by kiuri on 2007-10-02
Hi

I have Vista on my pc and just installed Ubuntu today, the thing is I can't find a way to configure my network connection. I go to  System &#10148; Administration &#10148; Networking to open the Network Settings dialog box and I select to put the settings manually and it opens up the network settings tab, but the only thing listed there is a dial up connection. Now heres the problem I have Adsl connection, and can't find a way to make a new connection to it. So I switched do the DNS TAB in network settings, putted the dns addresses (preferred and the alternate), and not surprisingly didn't work.
I searched online for it, but didn't find any how to. 
I noticed that Ubuntu does not recognize my inboard Lan adapter on the device manager, I searched for the drivers online but couldn't find it also, my motherboard is Intel Classic Series model: DG33FB.

I have a modem connected to a switch and my pc is connected to the switch
Here are my network details from Vista:

**internet protocol version 4**

ip address: 192.168.2.2
subnet mask: 255.255.255.0
default gateway: 192.168.2.1


DNS:
preferred address 125.22.47.125
alternate address 202.56.250.5



**internet protocol version 6**
ip address:automatic


DNS:
automatic




I've read "Beginning Ubuntu from novice to professional" and couldn't find a solution to my problem.
I think that I have to change my static IP information and the subnet, but I don't know how.

One more question: How do I run the gcc compiler on Ubuntu?

Thanks for helping in advance, sorry for my bad English!

---

### Post by greenstar on 2007-10-02
I'd check the BIOS and make sure that your on-board NIC is enabled. Then go to your Network applet and enable DHCP in properties.

Let's leave the gcc compiler for when your linux skills are more advanced.

Greenstar

---

### Post by noob12 on 2007-10-02
kiuri: You have the 82566DC LAN chipset.  Take a look at this thread for instructions:  [http://ubuntuforums.org/showthread.php?t=551720](http://ubuntuforums.org/showthread.php?t=551720)

---

### Post by kiuri on 2007-10-05
Thanks a lot noob12 it worked, and I am online now, but I have another problem lol, I was trying to install graphic drivers for my nvidia and i used the line $ sudo apt-get install nvidia-glx

sudo nvidia-xconfig --add-argb-glx-visuals --composite

Now you need to restart your X by logging out and in or by pressing ctrl+alt+backspace

I preesed ctrl+alt+backspace and it appeared an error message that it couldnt configure well, and now every time I log on to Ubuntu it show's the same error message and it also opens up the console and I can't find a way to get in.
Please help

---

### Post by noob12 on 2007-10-05
Glad to hear you go the networking working.  Unfortunately I don't know much about your desktop issue.

You should use the "Desktop Environments" forum for help with this sort of thing.

They'll probably set you straight much more quickly than I can.

---

### Post by kiuri on 2007-10-06
hello, Im here again cause I have a problem with the network again, I installed that way that you said and it worked but I updated my pc and it stopped working again, it only recognizes modem connection. I tried to reinstall and it didnt work heres the console:
I updated using this commands:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

after restarting it wasnt working again
--------------------------------------------------------------------------------------------------------------
kiuri@kiuri-desktop:~$ sudo apt-cdrom add
Password:
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
E: Failed to mount the cdrom.
kiuri@kiuri-desktop:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [b0eec9ebb2f73cb755ea5ff17b89a5e4-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called: 
'Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)'
Copying package lists...gpgv: Signature made Sun 15 Apr 2007 07:22:01 PM IST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.
kiuri@kiuri-desktop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kiuri@kiuri-desktop:~$ cd /tmp
kiuri@kiuri-desktop:/tmp$ dpkg --install linux-headers-2.6.20-15-generic_2.6.20-15.27_i386.deb
dpkg: requested operation requires superuser privilege
kiuri@kiuri-desktop:/tmp$ sudo dpkg --install linux-headers-2.6.20-15-generic_2.6.20-15.27_i386.deb
(Reading database ... 112911 files and directories currently installed.)
Preparing to replace linux-headers-2.6.20-15-generic 2.6.20-15.27 (using linux-headers-2.6.20-15-generic_2.6.20-15.27_i386.deb) ...
Unpacking replacement linux-headers-2.6.20-15-generic ...
Setting up linux-headers-2.6.20-15-generic (2.6.20-15.27) ...
kiuri@kiuri-desktop:/tmp$ cd /tmp
kiuri@kiuri-desktop:/tmp$ tar xvfz e1000-7.6.5.tar.gz
e1000-7.6.5/
e1000-7.6.5/src/
e1000-7.6.5/src/Makefile
e1000-7.6.5/src/e1000.h
e1000-7.6.5/src/e1000_80003es2lan.c
e1000-7.6.5/src/e1000_80003es2lan.h
e1000-7.6.5/src/e1000_82540.c
e1000-7.6.5/src/e1000_82541.c
e1000-7.6.5/src/e1000_82541.h
e1000-7.6.5/src/e1000_82542.c
e1000-7.6.5/src/e1000_82543.c
e1000-7.6.5/src/e1000_82543.h
e1000-7.6.5/src/e1000_82571.c
e1000-7.6.5/src/e1000_82571.h
e1000-7.6.5/src/e1000_api.c
e1000-7.6.5/src/e1000_api.h
e1000-7.6.5/src/e1000_defines.h
e1000-7.6.5/src/e1000_ethtool.c
e1000-7.6.5/src/e1000_hw.h
e1000-7.6.5/src/e1000_ich8lan.c
e1000-7.6.5/src/e1000_ich8lan.h
e1000-7.6.5/src/e1000_mac.c
e1000-7.6.5/src/e1000_mac.h
e1000-7.6.5/src/e1000_main.c
e1000-7.6.5/src/e1000_manage.c
e1000-7.6.5/src/e1000_manage.h
e1000-7.6.5/src/e1000_nvm.c
e1000-7.6.5/src/e1000_nvm.h
e1000-7.6.5/src/e1000_osdep.h
e1000-7.6.5/src/e1000_param.c
e1000-7.6.5/src/e1000_phy.c
e1000-7.6.5/src/e1000_phy.h
e1000-7.6.5/src/e1000_regs.h
e1000-7.6.5/src/kcompat.c
e1000-7.6.5/src/kcompat.h
e1000-7.6.5/src/kcompat_ethtool.c
e1000-7.6.5/COPYING
e1000-7.6.5/README
e1000-7.6.5/ldistrib.txt
e1000-7.6.5/pci.updates
e1000-7.6.5/e1000.spec
e1000-7.6.5/e1000.7
e1000-7.6.5/SUMS
kiuri@kiuri-desktop:/tmp$ cd e1000-7.6.5/src
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ sudo cp /lib/modules/2.6.20-15-generic/kernel/drivers/net/e1000/e1000.ko ~/e1000-2.6.20-15-generic.orig.ko
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ make
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/tmp/e1000-7.6.5/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/e1000-7.6.5/src/e1000_main.o
  CC [M]  /tmp/e1000-7.6.5/src/e1000_82540.o
  CC [M]  /tmp/e1000-7.6.5/src/e1000_82542.o
  CC [M]  /tmp/e1000-7.6.5/src/e1000_82571.o
  CC [M]  /tmp/e1000-7.6.5/src/e1000_82541.o
  CC [M]  /tmp/e1000-7.6.5/src/e1000_82543.o
  CC [M]  /tmp/e1000-7.6.5/src/e1000_ich8lan.o
  CC [M]  /tmp/e1000-7.6.5/src/e1000_80003es2lan.o
  CC [M]  /tmp/e1000-7.6.5/src/e1000_mac.o
  CC [M]  /tmp/e1000-7.6.5/src/e1000_nvm.o
  CC [M]  /tmp/e1000-7.6.5/src/e1000_phy.o
  CC [M]  /tmp/e1000-7.6.5/src/e1000_manage.o
  CC [M]  /tmp/e1000-7.6.5/src/e1000_param.o
  CC [M]  /tmp/e1000-7.6.5/src/e1000_ethtool.o
  CC [M]  /tmp/e1000-7.6.5/src/kcompat.o
  CC [M]  /tmp/e1000-7.6.5/src/e1000_api.o
  LD [M]  /tmp/e1000-7.6.5/src/e1000.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/e1000-7.6.5/src/e1000.mod.o
  LD [M]  /tmp/e1000-7.6.5/src/e1000.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ sudo install -D -m 644 e1000.ko /lib/modules/2.6.20-15-generic/kernel/drivers/net/e1000/e1000.ko
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ 
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ sudo modprobe e1000
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ sudo /etc/init.d/networking/restart
sudo: /etc/init.d/networking/restart: command not found
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ echo "e1000" | sudo tee -a /etc/modules
e1000
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ cd /tmp/e1000-7.6.5/src
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ sudo cp /lib/modules/2.6.20-16-generic/kernel/drivers/net/e1000/e1000.ko ~/e1000-2.6.20-16-generic.orig.ko
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ 
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ sudo install -D -m 644 e1000.ko /lib/modules/2.6.20-16-generic/kernel/drivers/net/e1000/e1000.ko
kiuri@kiuri-desktop:/tmp/e1000-7.6.5/src$ 
--------------------------------------------------------------------------------------------------------------

---

### Post by kiuri on 2007-10-06
I restarted my pc, and loged in with vista, then I restarted again and logged in with ubuntu and my network is now working fine again... strange...
thanks anyway

---

### Post by noob12 on 2007-10-06
When you upgrade from 2.6.20-15 to 2.6.20-16, the custom modules you installed in -15 don't go with you.  There is the second section in that same HOWTO which describes what you need  to install the driver into the 2.6.20-16 kernel once you upgrade.

---

