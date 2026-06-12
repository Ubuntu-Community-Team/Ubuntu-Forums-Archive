---
title: "atheros 5007"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by pstrbrc on 2008-09-23
specifics:
Toshiba Satellite
dual boot: Ubuntu 8.04/Win Vista
Atheros Ar5007 wireless (but shows up as Atheros 242x)

I found these instructions on "UbuntuGeek"
> For i386 Users

First go to System&#8211;>Administration&#8211;>Hardware Drivers&#8221; and disable by un-ticking the following option
Atheros Hardware Access Layer (Hal)
Then Reboot your system.
Preparing your system
sudo apt-get install build-essential
Then open the terminal from Applications&#8211;>Accessories&#8211;>Terminal and copy the following command
wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
tar xfz madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007
make
sudo make install
sudo modprobe ath_pci
sudo reboot
That&#8217;s it now your wireless should work without any problem.

Here's what I got-
> pstrbrc@pstrbrc-laptop:~$ sudo apt-get install build-essential
[sudo] password for pstrbrc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
pstrbrc@pstrbrc-laptop:~$ wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
--10:33:31--  [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
           => `madwifi-ng-r2756+ar5007.tar.gz.2'
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 485 [application/x-gzip]

100%[====================================>] 485           --.--K/s             

10:33:31 (28.67 MB/s) - `madwifi-ng-r2756+ar5007.tar.gz.2' saved [485/485]

pstrbrc@pstrbrc-laptop:~$ tar xfz madwifi-ng-r2756+ar5007.tar.gz
pstrbrc@pstrbrc-laptop:~$ cd madwifi-ng-r2756+ar5007
pstrbrc@pstrbrc-laptop:~/madwifi-ng-r2756+ar5007$ make
make: *** No targets specified and no makefile found.  Stop.
pstrbrc@pstrbrc-laptop:~/madwifi-ng-r2756+ar5007$ 
 

Obviously I don't understand what I did wrong, and I don't understand what it means when it says "No targets specified and no makefile found."
What did I miss?
:confused:
(I'm getting tired of using the :confused: emoticon. I can't wait 'til I get better at this!!!)

---

### Post by shanix on 2008-09-23
Perhaps what you need is:

[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3861-20080903.tar.gz)

For more information:
[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

---

### Post by windozehater on 2008-09-23
first reenable hal 

they require an active internet connection, so walk your computer over to the router and hook up the ethernet. Open a terminal and do these commands, each in order and in turn.
Code:

sudo apt-get install build-essential linux-headers-generic
wget [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)
tar zxvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-(current build whereever you extracted it)



make
sudo make install
sudo modprobe ath_pci
sudo reboot
 
you will have to clean and remake with each new kernel.

---

### Post by pstrbrc on 2008-09-23
> **windozehater said:**
> first reenable hal 

they require an active internet connection, so walk your computer over to the router and hook up the ethernet. Open a terminal and do these commands, each in order and in turn.
Code:

sudo apt-get install build-essential linux-headers-generic
wget [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)
tar zxvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-(current build whereever you extracted it)



make
sudo make install
sudo modprobe ath_pci
sudo reboot
 
you will have to clean and remake with each new kernel.

Yes, I have it hooked up to my router. But I think I might be seeing part of my problem. What are you saying that I'm not understanding?
> cd madwifi-(current build whereever you extracted it)

Is this part of 
> "No targets specified and no makefile found."  ?

Which I guess is a larger question about understanding Linux filing system after living my entire computering life with That Other One. 

edit: I just went into my Home file and found the answer! The subfolder Home/madwifi-ng-r2756+ar5007 has just a "read me" that tells me what both of you are saying! 
OK, one more try!!!!![IMG]http://ubuntuforums.org/images/smilies/eusa_wall.gif[/IMG]

---

### Post by pstrbrc on 2008-09-23
Hot dog! One step closer!
OK, everything ran, got no "Hey,dummy!" messages. But...
This computer has a manual switch to turn the wireless on. But no indication that I have a wireless connection. 
> pstrbrc@pstrbrc-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:40:67:83
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.2.3 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: de:d2:73:c2:b8:5a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
pstrbrc@pstrbrc-laptop:~$ 



Does any of that mean anything to anybody?
:confused:
What am I missing now?
:confused:

---

### Post by pstrbrc on 2008-09-23
OK. When I go to the Ubuntu Documentation site 
[https://help.ubuntu.com/8.04/internet/C/troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html)
I find this:
> Check for device recognition

   1.

      Open Device Manager (System &#8594; Preferences &#8594; Hardware Information).
   2.

      Check to see the hardware is recognised if it is then the section called “Check for driver”
   3.

      If your device is not displayed then there may be a hardware problem. Ensure if it is PCMCIA or PCI that it is inserted correctly.



Except that I have no {system/preferences/hardware information} 

 under {system/administration/network} I only show a wired connection and a point-to-point (dialup) connection, no wireless. 
What's my next step?

---

