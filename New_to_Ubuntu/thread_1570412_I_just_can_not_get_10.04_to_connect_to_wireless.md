---
title: "I just can not get 10.04 to connect to wireless"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by ex-para on 2010-09-08
I just can not get 10.04 to connect to wireless with the try it before installing. The computer is a dell inspiron with vista and the connection is turned on. When I tried intrepid on this computer it connected no problem and when I tried 10.04 on a computer with a wireless card it worked so why the hassle. Any suggestions please.

---

### Post by JohnHeikkila on 2010-09-08
Could you run "sudo lshw -C network" and copy the output in a code window please?
And by running I mean open console, etc.

---

### Post by ex-para on 2010-09-08
ubuntu@ubuntu:~$ sudo lshw -C network 
  *-network               
       description: Network controller 
       product: BCM4312 802.11b/g 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 
       resources: irq:17 memory:f69fc000-f69fffff 
  *-network 
       description: Ethernet interface 
       product: 88E8040 PCI-E Fast Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       logical name: eth0 
       version: 13 
       serial: 00:25:64:4d:d1:58 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256) 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:26:5e:54:53:aa 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
ubuntu@ubuntu:~$

---

### Post by Chris1274 on 2010-09-08
I have an Inspiron too. From 9.1 on, Ubuntu no longer supports its Broadcom wireless card out of the box. That's why I keep a Jaunty liveUSB handy in case the HDD goes, that way I can still boot up and have a working wireless card.

In any case, your best bet is to find a wired connection, run the update manager, and then download the Broadcom STA driver through the hardware manager.

---

### Post by bredman on 2010-09-08
Your problem is the driver for the BCM4312 WiFi.

For legal reasons, Ubuntu cannot distribute the firmware for this device by default, but it is officially supported, as long as you install it yourself.

For more details, see [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

To summarize for Ubuntu, you only need to enter one command
sudo apt-get install b43-fwcutter

I can confirm that a BCM4312 works on Unbuntu 10.04 after this command.

---

### Post by ex-para on 2010-09-08
Thanks for replies but this time it did not work and i have tried twice.
 
ubuntu@ubuntu:~$ sudo apt-get install b43-fwcutter 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following NEW packages will be installed: 
  b43-fwcutter 
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded. 
Need to get 0B/17.9kB of archives. 
After this operation, 115kB of additional disk space will be used. 
Preconfiguring packages ... 
Selecting previously deselected package b43-fwcutter. 
(Reading database ... 129801 files and directories currently installed.) 
Unpacking b43-fwcutter (from .../b43-fwcutter_012-1build1_i386.deb) ... 
Processing triggers for man-db ... 
Setting up b43-fwcutter (1:012-1build1) ... 
--2010-09-08 16:45:11--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) 
Resolving downloads.openwrt.org... failed: Name or service not known. 
wget: unable to resolve host address `downloads.openwrt.org' 
dpkg: error processing b43-fwcutter (--configure): 
 subprocess installed post-installation script returned error exit status 4 
Errors were encountered while processing: 
 b43-fwcutter 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
ubuntu@ubuntu:~$

---

### Post by anewguy on 2010-09-08
you can also install the firmware cutter directly off the installation Cd (LiveCD) for ubuntu.  It located in the /pool/main/b folder on the CD.

The easiest way, though, to get your wireless working is:

- temporarily hard-wire your PC to the router

- in a terminal window (Applications/Accessories/Terminal) type:

sudo apt-get update <press enter>

- when that finishes, check in System/Administration/Hardware Drivers and see if a driver for Broadcom wireless shows - if so, enable it

- physically disconnect the hard-wired connection to the router

- right-click on the network manager icon - be sure "Enable Wireless" is checked

- left-click on the the network manager icon - see if wireless networks show now.


Dave

---

### Post by ex-para on 2010-09-09
Followed the instructions OK and it seemed to go correctly then disconnected the wire went to the wireless icon and my reuter details where showing so I added my details clicked connect. The icon is showing it is trying to connect but never does and  repeatedly asks for my HomeHub details. I have searched for an answer on the net but what I have seen is all different answers. So a little more information might get me connected if possible please. I am still on the try it not full install.

---

### Post by bredman on 2010-09-09
It looks like your wireless is almost working.

Please post the result of the command
iwconfig

Have you set the security settings the same on the PC and the wireless router? Note that BCM devices are notoriously bad at WEP, so use WPA or WPA2 if possible.

---

### Post by ex-para on 2010-09-09
ubuntu@ubuntu:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     IEEE 802.11bg  ESSID:off/any  

          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   

          Tx-Power=20 dBm   

          Retry  long limit:7   RTS thr:off   Fragment thr:off

          Power Management:off

          

ubuntu@ubuntu:~$ 

WPA and WPA2 is showing WEP is greyed out.
I have reconnected the wire to send this.

---

### Post by JohnHeikkila on 2010-09-09
off/any = Not connected

---

### Post by Miljet on 2010-09-09
I have been fighting this same problem for over a week on my granddaughter's Dell Inspiron 1525. It has the Broadcom BCM4312 [14e4:4315] chipset. Her wireless worked for several months after upgrading to 10.04, then suddenly quit.

I have read endless threads on problems with this and other Broadcom chips and tried everything I could find. At the moment, the most promising solution I have found involves the following command
```
sudo apt-get install --reinstall bcmwl-kernel-source 
```
It seems that several people had success with this. I haven't had my granddaughter try this yet. She lives in another state and all troubleshooting has to be over the phone. 

If someone does solve this, it sure would be nice if they post what worked instead of just letting the thread die out.

---

### Post by dcsoldschool53 on 2010-09-09
I have a question? What network manager are you using? Is it Wicd for wireless?

---

### Post by ex-para on 2010-09-09
Afraid it did not work, I am starting to wear a bit thin on this as it is taking to much of my time. Its no fun struggling with an OS like this as there is obviously something not right with it. I booted it up  OK on a older laptop with a wireless card  and it connected automatically but before long if I don't get it working I will just have to install another Linux system, I know Intrepid works OK.

---

### Post by ex-para on 2010-09-09
I think its Applet 0.8

---

### Post by philinux on 2010-09-09
> **ex-para said:**
> Afraid it did not work, I am starting to wear a bit thin on this as it is taking to much of my time. Its no fun struggling with an OS like this as there is obviously something not right with it. I booted it up  OK on a older laptop with a wireless card  and it connected automatically but before long if I don't get it working I will just have to install another Linux system, I know Intrepid works OK.

Unfortunately Intrepid has reached end of life and is no longer supported.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by ex-para on 2010-09-09
Intrepid will be whole lot better than a system that will not work.

Can anyone tell me if I can buy a wireless card that will fit into this Dell Inspiron maybe I can have it working that way. I have a few Linux friendly cards but no place to put them in this laptop as they are to big.

---

### Post by Miljet on 2010-09-09
Actually I was thinking of getting my granddaughter a USB wireless device (with something other that a Broadcom chipset) and seeing if that works.

---

### Post by GaryTheCat on 2010-09-09
I've got a dell inspiron too - I had the same problems initially that took me days to crack, I found the advice (somewhere in these fora) - but now can't find it to connect to your router by ethernet and:

```
sudo apt-get update
```

and then look at:

Administration ---> hardware drivers

Select the right one for your broadcom card and away you go

---

### Post by dcsoldschool53 on 2010-09-09
Ok what I want you to do is right click on your network manager icon and click about. This will tell you the name of the network manager that you are using. With ubuntu 10.04 I had to install Wicd. If you do not see wicd, download and install it. Ubuntu 10.04 does not automatically install the program for wireless. So if you just install ubuntu, the wireless program that comes with the download does not work. It will look like it is working but it don't. Check to see which one you have.

---

### Post by ex-para on 2010-09-10
As as I said before I have Applet, any tips on installing it please?

---

### Post by dcsoldschool53 on 2010-09-10
Before I tell you how to do this, I want you to understand something. If you install one network manager, you will need to uninstall the other one. They may conflict with each other if you don't do it. Also you need to have internet access to do it. If you can connect that pc to a wired network, it will work just fine. To install WICD try this at the terminal. 

sudo apt-get install wicd

To uninstall nettwork manager, you can either remove it through Synaptic Package Manager or, in a terminal type

sudo apt-get remove network-manager

after you have done this, reboot your system.I hope this helps.

---

### Post by ex-para on 2010-09-10
That it why I asked for tips as I had seen this on some website and when tried it I got the application is in use. So now I will shortly try the wicd.

---

### Post by ex-para on 2010-09-11
This is as far as I got with this, everything regarding 10.04 goes the same way. 

ubuntu@ubuntu:~$ sudo apt-get install wicd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wicd
ubuntu@ubuntu:~$

---

### Post by dcsoldschool53 on 2010-09-11
ok you can try Synaptic Package Manager. If that does not work, try to seach for it in a search engine. I know that Ubuntu has a site called packages.ubuntu or something like that. One of those should work for you.

---

### Post by ex-para on 2010-09-27
I finally got to grips with my problem, and wireless on 10.04 is now working. First I installed 8.10 dual boot with Vista because I could get a connection and then Adobe Flash would not install and people were telling me it was obsolete so removed it and fully installed 10.04  dual boot if it would work or not. I  followed Dave's post

The easiest way, though, to get your wireless working is:

- temporarily hard-wire your PC to the router

- in a terminal window (Applications/Accessories/Terminal) type:

sudo apt-get update <press enter>

- when that finishes, check in System/Administration/Hardware Drivers and see if a driver for Broadcom wireless shows - if so, enable it

- physically disconnect the hard-wired connection to the router

- right-click on the network manager icon - be sure "Enable Wireless" is checked

- left-click on the the network manager icon - see if wireless networks show now.


Dave 

but I used the Sata drive not the first one on the list and it worked.

---

