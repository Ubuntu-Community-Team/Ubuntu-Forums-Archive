---
title: "Wireless network icon not shown in Network Settings. HP AMD Turion64"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by aiko.uda on 2008-09-02
Hi. I installed Ubuntu few days ago. My computer is HP Pavilion Entertainment PC AMD Turion 64.

Now I cannot enable wireless internet because the wireless icon is not shown in the Network setting. When I go to Network Setting by clicking small icon with two screen beside the date and time, I have only two options: Wired connection or Point to point connection. How can I get the wireless device in here?

Here are some info based on the trouble shooting section in Help doc.
 (I cannot understand them, but maybe you can help me with this.)

I could not check for device recognition. There is no Device Manager under system>Preferences>Hardware Information. I cannot see Hardware Information in the menu.

Result for sudo lshw -C network
aiko@aiko-laptop:~$ sudo lshw -C network
[sudo] password for aiko: 
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:09:4f:38
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.2.82 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

Result for iwconfig
aiko@aiko-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Result for ifconfig
aiko@aiko-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:09:4f:38  
          inet addr:192.168.2.82  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe09:4f38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3441 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5003959 (4.7 MB)  TX bytes:444169 (433.7 KB)
          Interrupt:220 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6900 (6.7 KB)  TX bytes:6900 (6.7 KB)

Result for sudo dhclient if_name
aiko@aiko-laptop:~$ sudo dhclient if_name
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
if_name: ERROR while getting interface flags: No such device
if_name: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

Last thing. I also tried NDISWrapper. I installed ndisgtk and open the application. However, I cannot "obtain the Windows Driver" nor locate (or don't know even where to look for) the .inf file.

I really appreciate your help!

---

### Post by Blackcabs on 2008-09-02
You could quickly unplug your wired connection,, then see if network manager shows it ??. Apparently there is an issue with network manager detecting the wifi card if it has a wired connection to use,, as it will go the wired route first.

---

### Post by aiko.uda on 2008-09-02
Thank you for your reply.

Initially, I did not have the cable plugged in when I installed. After installation, the wireless icon did not show and I was doing help search using other computer.

I plugged in the cable yesterday as I did not want to retype the results from terminal function.

Do you see anything else that I am doing wrong???

Thanks

---

### Post by Blackcabs on 2008-09-02
Your system is not loading the driver for your card. I had alook at broadcoms site but i couldn't find one,,However we can download it from hp but i need to know the exact HP model that you have and did it use to contain Win XP..There is more than likley a linux driver for it but i dont know what its called and seeing that you have already chosen the NDISWrapper route we might as well carry on.

---

### Post by aiko.uda on 2008-09-02
Ok, this is what I found on a sticker in the back.

Product:HP Pavilion dv9700
s/n:CNF8042CL4
p/n:KC339UA#ABC

Is this what you need?

---

### Post by aiko.uda on 2008-09-02
Sorry. One more thing on the right hand corner.

dv9726ca

---

### Post by aiko.uda on 2008-09-02
By the way, this computer used to have Windows Vista not XP.

Does this make a difference?

---

### Post by Ayuthia on 2008-09-03
You might try the driver option in step 2d from this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

It is for ndiswrapper.  Your card can use the ndiswrapper option and the wl driver from Broadcom.  To try the Broadcom card, you can either try the testing version:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

Or you can try and install the driver directly from Broadcom's site:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
The instructions are in the readme link.

Hope that helps.

---

### Post by Blackcabs on 2008-09-03
> **Ayuthia said:**
> You might try the driver option in step 2d from this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

It is for ndiswrapper.  Your card can use the ndiswrapper option and the wl driver from Broadcom.  To try the Broadcom card, you can either try the testing version:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

Or you can try and install the driver directly from Broadcom's site:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
The instructions are in the readme link.

Hope that helps.

Thanks for the links Ayuthia,, 

Ok aiko.uda  have a read through those links,,But basically its as follows,,Although if you are unsure of anything refer to those links
Open a terminal then type these commands Starting at number 1 Ignore the driver that i have uploaded with this post
as its to new to work correctly

1  echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
2  sudo apt-get install ndiswrapper-utils-1.9
3  mkdir ~/bcm43xx; cd ~/bcm43xx
4  sudo apt-get install cabextract
5  wget [ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe)
6  cabextract sp33008.exe
7  unzip bcmwl5.inf.zip
8  sudo ndiswrapper -i bcmwl5.inf  
9  sudo depmod -a
10 sudo modprobe ndiswrapper
11 sudo cp /etc/network/interfaces /etc/network/interfaces.orig
12 echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
13 sudo ndiswrapper -m
14 echo 'ndiswrapper' | sudo tee -a /etc/modules
15 echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant


Hope all goes well Blackcabs

---

### Post by Ayuthia on 2008-09-03
> **Blackcabs said:**
> Thanks for the links Ayuthia,, 

Ok aiko.uda  have a read through those links,,But basically its as follows
Open a terminal then type these commands Starting at number 1 before you do this copy the driver to your Desktop that i have added to this post.You can miss out commands 1 & 2 if you have already extracted

1  cd Desktop
2  unzip bcmwl6.inf.zip
3  sudo ndiswrapper -i bcmwl6.inf  
4  sudo depmod -a
5  sudo modprobe ndiswrapper
6  sudo cp /etc/network/interfaces /etc/network/interfaces.orig
7  echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
8  sudo ndiswrapper -m
9  echo 'ndiswrapper' | sudo tee -a /etc/modules
10 echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

I had a look at HP'S site and downloaded the latest windows driver for your notebook ,,thats why it differs from the one listed in the above links.
Hope all goes well Blackcabs
You are going to need to use the driver from the no-fluff link.  The Vista (bcmwl6) drivers do not work with ndiswrapper yet.  Also, you might want to follow the information in the no-fluff link.  There are some information in blacklisting that will be needed to make it work.

---

### Post by Blackcabs on 2008-09-03
Thanks for the info Ayuthia I will edit my post,,did not realise that (bmcwl6) driver does not work with ndiswrapper yet. Thanks again

---

### Post by aiko.uda on 2008-09-03
Thank you both for the reply.

Blackcabs, I followed all the steps listed above and checked back on the Windows Wireless Drivers. It says "bcmwl6 Invalid Driver!" with a big red cross on it...

---

### Post by aiko.uda on 2008-09-03
Ok, Ayuthia, I was just reading the links you gaveme and I'm going to try the links here. Thank you

---

### Post by Blackcabs on 2008-09-03
[QUOTE=aiko.uda;5720233]Thank you both for the reply.

Blackcabs, I followed all the steps listed above and checked back on the Windows Wireless Drivers. It says "bcmwl6 Invalid Driver!" with a big red cross on it...[/QUOTE

I am sorry aiko.uda i updated my most as soon as i was informed that the bmcl6 driver was to new to work with nidswrapper yet,, but you had already started before seeing my correction. Sorry again

---

### Post by aiko.uda on 2008-09-04
> **Blackcabs said:**
> I am sorry aiko.uda i updated my most as soon as i was informed that the bmcl6 driver was to new to work with nidswrapper yet,, but you had already started before seeing my correction. Sorry again

Hi Blackcabs, no worries. Thank you for helping me out. Honestly, if I did not read your directions first, I would not have not known that I was supposed to type in those commands into Terminal line by line...

Thanks

---

### Post by Blackcabs on 2008-09-05
> **aiko.uda said:**
> Hi Blackcabs, no worries. Thank you for helping me out. Honestly, if I did not read your directions first, I would not have not known that I was supposed to type in those commands into Terminal line by line...

Thanks

No problem i enjoy trying to help others,,I don't profess to know everything, but sometimes people in the forums assume that everyone knows how to type in commands !!! So i always try to make instructions as simple as possible..Considering i have only been using linux for two months,,I am pretty proud of myself:biggrin:

Good luck for the future Ubuntu is AWESOME 
Blackcabs

---

