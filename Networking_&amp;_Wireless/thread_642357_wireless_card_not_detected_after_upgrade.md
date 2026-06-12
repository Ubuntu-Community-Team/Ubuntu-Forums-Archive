---
title: "wireless card not detected after upgrade"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by DocForbin on 2007-12-16
After upgrading from 7.04 to 7.10 my wireless card no longer appears in network settings. This is a Thinkpad t43 and according to lscpi the built in wireless card is Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05). I've never had a problem in previous versions and am not sure where to start, any help would be greatly appreciated.

---

### Post by DocForbin on 2007-12-16
When I run lshw I get

   *-network UNCLAIMED
	description: Network controller
	product: PRO/Wireless 2915ABG Network Connection
	vendor: Intel Corporation
	physical id: 2
	bus info: pci@0000:0b:02.0
	version: 05
	width: 32 bits
	clock: 33MHz
	capabilities: cap_list
	configuration: latency=64 maxlatency=24 mingnt=3

Does UNCLAIMED mean the driver isn't installed?

---

### Post by DocForbin on 2007-12-16
Some more info... My /etc/network/interfaces looked like this after the upgrade:

auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

auto eth2

Per another thread, I tried replacing with just 

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

Rebooted and still no luck.

---

### Post by DocForbin on 2007-12-16
So I just made a live CD and wireless works fine when I boot from it. I tried copying the /etc/network/interfaces used from the boot CD, but am getting nowhere :(

---

### Post by DocForbin on 2007-12-16
Success!

sudo apt-get install linux-ubuntu-modules-2.6.22-14-386

rebooted and wireless is back

---

### Post by gilf on 2007-12-16
That's the brute force method of solving the problem. Glad you fixed your system.

The basic problem was probably caused however when you modified your initial HD install. Since that is what the LiveCD session ignores and corrects. If the LiveCD session works, a proper install to HD without modifying the network settings manually will also work the same way.

The /etc/network/interfaces file you presented above had several problems.

An additional likely scenario occurred when you tried to correct it from the liveCD version, 

There's a good liklihood you may have omitted the first slash in editing:

/etc/network/interfaces

since you advised another person in another thread to run:

sudo gedit etc/network/interfaces   without the slash.

This results in attempting to edit a file in the user's home directory. While it can be written, it won't affect network operation.

I add this note only so people don't necessarily assume that reloading Ubuntu is the cure for wifi network ills. Though it would be necessary for a corrupted install.

I'm happy your network problems are solved, in any case!

---

### Post by DocForbin on 2007-12-16
> **gilf said:**
> There's a good liklihood you may have omitted the first slash in editing:

/etc/network/interfaces

since you advised another person in another thread to run:

sudo gedit etc/network/interfaces without the slash.
naw, that was just a typo in the other post

btw, I hadn't modified my network settings in any way after the upgrade. I edited the interfaces file to match that of the live CD in troubleshooting the issue. Wireless never showed up in network settings after the upgrade.

---

### Post by gilf on 2007-12-16
To understand further what was wrong, can you post your current interfaces file?

Thanks!

---

### Post by Goodkimchee on 2007-12-16
Since this is basically the problem that I'm having, i thought I would just jump in.  I've been reading several threads, and most have suggested that I change my Network Manager.  One said that changing from the network manager to wicd had helped them, and I tried that but nothing.  The restricted driver works (Broadcom 43xx), and with wicd I can detect the network, but I can't log on!  

This is quite vexing.  Any and all help would be most appreciated.

---

### Post by DocForbin on 2007-12-16
> **gilf said:**
> To understand further what was wrong, can you post your current interfaces file?

Thanks!

auto lo
iface lo inet loopback

---

### Post by gilf on 2007-12-16
Well that's pretty simple. 

That's what a wired connection looks like. But you did say yours was a built-in wireless connection, right?

---

### Post by aldo_m on 2007-12-23
you know im having the same problem . i did the last update and lost the wg511t when it  worked fine before the update. i have just one light flashing on the card . but if i use my backtrack live cd it boots up and works. im tring what thread maker did with the kernal.
ah damn the link is down" sudo apt-get install linux-ubuntu-modules-2.6.22-14-386 " not  working man i realy need to get thisto work need help
. *-network UNCLAIMED
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=28 mingnt=10
nsa@Nsa:~$ sudo modprobe ath_pci
[sudo] password for nsa:
FATAL: Module ath_pci not found.

---

### Post by geek_Man on 2007-12-23
I'm having a similar problem. My (internal) wireless card is an Intel Corporation PRO/Wireless 3945ABG (according to lspci, but you never know...). lshw says 
         *-network
                description: Network controller
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=ipw3945 latency=0 module=ipw3945

I tried doing the kernel update and changing the interfaces file, but neither of those helped...

---

