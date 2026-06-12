---
title: "Wireless network - SSID recognised, Even with no encryption I get no internet!"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by chickyd on 2007-07-18
OK, so I've installed Ubuntu but getting no internet! - very annoying!

I have no other means to get on the internet so please help!

Ubuntu sees my wireless card as 'ra0' however in network devices it says 'ra0' is an 'Unkown Device'...

My network SSID is seen and I am getting 4 bars in the top right hand of the screen (two of which are blue) and when i move my mouse over them i get a message 'Connection to wireless network "MY SSID" 50%'... but I can't get on the internet.

I've tried playing with the security of my network and last night resorted to taking all the encryption off all together.. still no internet! 

I have no firewall (firestarter) installed.

I am using a Belkin wireless PCI card.

Anyone able to offer some advice? I would greatly appreciate it if you explained anything in detail as I'm new to the Linux file structure.

---

### Post by kevdog on 2007-07-18
Can you give more details about your card such as:
lshw -C network

Did you install any drivers, or make any manual configurations to the /etc/network/interfaces file?

---

### Post by chickyd on 2007-07-18
I am a complete newbie with Ubuntu - is there something i should type into the terminal to get this information back for you? I have installed no drivers - wireless card was recognised by Ubuntu on first boot - and have been switching between roaming and manual configurations to try and make it work - i have reverted to roaming though as I have removed my network encryption to get ini working initially first. I have therefore just been clicking the network connection icon at the top right, selecting my network, and then waiting... but nothing happens.. not even an error.

Anything?

---

### Post by kevdog on 2007-07-18
Type 

lshw -C network

at command prompt, cut and paste output.  There are going to be a lot of things we are going to try.  All the commands will be at the command prompt.

---

### Post by chickyd on 2007-07-18
> **kevdog said:**
> Type 

lshw -C network

at command prompt, cut and paste output.  There are going to be a lot of things we are going to try.  All the commands will be at the command prompt.

I will do this as soon as I get back from work tonight.. many thanks for your help!!.. will update this thread as soon as it's done!...

---

### Post by js.opdebeeck on 2007-07-22
Same problem for me on Gutsy ...

Empty Encryption Wifi not available to connect . (Dell D630)

I can see the hotspots ... I can connect to WPA or WEP but when the SSID is a non secured access point (Hotel, Airport for HTTP access ...) the process is running but hang after some seconds .

lshw -C network =

  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:67:7c:d6
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.1mp firmware=14.2 1:0 () ip=192.168.182.8 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g

See the Launchpad discussion related to this ... [https://bugs.launchpad.net/ubuntu/gutsy/+source/network-manager/+bug/121439](https://bugs.launchpad.net/ubuntu/gutsy/+source/network-manager/+bug/121439)

Js

---

