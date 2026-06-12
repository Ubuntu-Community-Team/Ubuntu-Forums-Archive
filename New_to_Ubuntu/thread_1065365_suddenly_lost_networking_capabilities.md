---
title: "suddenly lost networking capabilities"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by webmiester on 2009-02-09
Hi guys,

Ive installed Ubuntu 8.10 on my MSI wind u100x netbook PC on a dual boot configuration with Windows.

Everything was working fine until last night when my ubuntu wouldnt connect to my LAN and the wifi hardware wasnt even detected.  Windows on the otherhand wouldnt even load, Windows would just suddenly turn into the BSOD while loading, then restart again...

I was at a lost as I couldnt get online...  Then I tried loading my other startup options:

GRUB would give me several options to boot:
UBUNTU 8.10, kernel 2.6.27-11-generic
UBUNTU 8.10, kernel 2.6.27-11-generic (recovery mode)
UBUNTU 8.10, kernel 2.6.27-9-generic
UBUNTU 8.10, kernel 2.6.27-9-generic (recovery mode)
UBUNTU 8.10, kernel 2.6.27-7-generic
UBUNTU 8.10, kernel 2.6.27-7-generic (recovery mode)
Other Operating Systems:
Windows XP Home

The networking would be totally off when using the UBUNTU 8.10, kernel 2.6.27-11-generic startup options (on both normal and recovery modes)...I go through my settings and I find that UBUNTU doest even recognize/find my LAN card nor my wifi card :( :( :(

however, when I tried the UBUNTU 8.10,kernel 2.6.27-9-generic startup option, it would load and everything would work perfectly!  This is what I am using now to connect to the internet and write you guys with.

Can someone plese tell me what is the difference between these two modes and tell me please if you have any theories on my problem.  Thank you so much!

---

### Post by tarps87 on 2009-02-10
The difference between these two:
UBUNTU 8.10, kernel 2.6.27-11-generic
UBUNTU 8.10, kernel 2.6.27-7-generic
would be the kernel, this is efectivaly the bit Ubuntu runs on, it is inbetween the hardware and the aplications. As for the diffrence between the kernals I can't rember where to find that but I'm sure someone else will.
How did you look to see if Ubuntu reconised the hardware? Also how far did windows get before the BSOD? The update should not have effected the windows install.

---

### Post by webmiester on 2009-02-12
Hi, I finally figured out the Windows issue...

I think I was looking around the BIOS settings and I tried to turn on AHCI support... That one really messed up my Windows XP...  the BSOD appears about 2 secods after the Windows XP loading screen shows up and the BSOD only lasts for a nanosecond before my computer reboots...  reinstalling was also futile as the installer didnt even recognize the hard disk.  By disabling the AHCI support, my windows went back to normal...

Now back at Linux...  I dont know how changing the AHCI would have affected my networking capabilities, since I lost it at the same time my windows went hey wire...  Usually upon boot-up, my computer would automatically connect to the home's wireless and wired connections as per the netowork monitor which appears on the top panel.  In this case though, it would automatically just appear that I am not connected to the network.  Clicking on the network manager, only the wired network option appears (No wireless), and when I do switch it on it tried to connect but fails.

When I click on the RutiLT WLAN Manager, it tells me that there is no hardware wifi available.

I just dont get it.  Why would my configuration suddenly change?  Also, if I really did mess up my BIOS or hardware settings, why did the other kernel version work while my usual kernel version didnt?  Also, I would like to ask why did my ubuntu installer install so many kernel versions?  Is that normal?  Thanks

Any ideas on how I can check on this?  BTW, when I go to System>Administration>Network Tools, my wifi and LAN cards dont appear under the devices...  what else can I do?

---

### Post by Neural oD on 2009-02-12
type sudo lshw -C network on the command line - this should tell u if they are there

---

### Post by tarps87 on 2009-02-12
> **webmiester said:**
> I just dont get it.  Why would my configuration suddenly change?  Also, if I really did mess up my BIOS or hardware settings, why did the other kernel version work while my usual kernel version didnt?  Also, I would like to ask why did my ubuntu installer install so many kernel versions?  Is that normal?

This could be as the new kernel is using different drivers or if you had to rebuild the kernel when installing the drivers (either manually or automatically), this will need to be done.
Usually there are a few kernel updates when a new release comes out, by adding each version in to the grub menu it means you can go back a version if something breaks.  You can expect most of the updates to be in the first month.
One way to look at it is 2.6.27 being the kernel version with the -11, -9, -7 being the update version
This is as clear in window as the kernel includes a lot more, where as in Linux the applications sit on top of the kernel.
To remove any unneeded entries in the boot list you can edit the grub menu:
```
sudo gedit /boot/grub/menu.lst
```

For the networking issue run the command in the post above and post the output here

---

### Post by webmiester on 2009-02-13
> **Neural oD said:**
> type sudo lshw -C network on the command line - this should tell u if they are there

---------- KERNEL without NETWORK -------------

webmiester@mobile-one-linux:~$ sudo lshw -c network 
[sudo] password for webmiester: 
  *-generic               
       description: Ethernet interface 
       product: Illegal Vendor ID 
       vendor: Illegal Vendor ID 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       logical name: eth0 
       version: ff 
       serial: 00:21:85:4d:11:28 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 66MHz 
       capabilities: bus_master vga_palette cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=255 link=yes maxlatency=255 mingnt=255 module=r8169 multicast=yes port=MII speed=100MB/s 
  *-network UNCLAIMED 
       description: Network controller 
       product: RTL8187SE Wireless LAN Controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       version: 22 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: latency=0 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: c2:a6:2c:af:88:33 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
webmiester@mobile-one-linux:~$


---------------KERNEL with NETWORK----------

*-network               

       description: Ethernet interface

       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 0

       bus info: pci@0000:01:00.0

       logical name: eth0

       version: 02

       serial: 00:21:85:4d:11:28

       size: 100MB/s

       capacity: 1GB/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.6 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

  *-network

       description: Wireless interface

       product: RTL8187SE Wireless LAN Controller

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: wlan0

       version: 22

       serial: 00:1d:92:ce:24:af

       width: 32 bits

       clock: 33MHz

       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless

       configuration: broadcast=yes driver=rtl8180 ip=192.168.1.5 latency=0 module=r8180 multicast=yes wireless=802.11b/g linked

  *-network DISABLED

       description: Ethernet interface

       physical id: 1

       logical name: pan0

       serial: 4e:49:53:47:fb:48

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

webmiester@mobile-one-linux:~$ 


------------------

Hi, what do you think?  It says "Illegal Vendor ID".... but it's the same computer...Any ideas?

---

### Post by tarps87 on 2009-02-16
I'm afraid all I can suggest is using 2.6.27-9-generic as it appears this is a bug with the latest kernel update, you can follow the progress of the bug here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/322916](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/322916)

I will keep looking for a work around and post back if I find one.

---

### Post by Mach1US on 2009-03-15
This should help , problem is new buggy driver.
[http://www.jamesonwilliams.com/hardy-r8168](http://www.jamesonwilliams.com/hardy-r8168)

---

### Post by cariboo on 2009-03-15
I'm using the same motherboard in my HTPC, and I get the same results for eth0 when running:

```
sudo lshw -C networkj
```

this is the output:

```
 sudo lshw -C network
  *-generic               
       description: Ethernet interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: ff
       serial: 00:1c:c0:8c:b4:70
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=255 link=yes maxlatency=255 mingnt=255 module=r8169 multicast=yes port=MII speed=100MB/s
```

I use a D-Link System WUA-1340 wireless adapter, as I've run out of ports on my router. 

When I do have a network cable hooked up, I get ip addresses on both adapters.

I'm running the following kernel:

```
uname -a
Linux likely 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linu
```

on the following release:

```
cat lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
```

Jim

---

### Post by webmiester on 2009-05-22
Hi guys,

now after months of using a lower kernel model, my wifi suddenly disappears again.  But this time, my LAN still works.  I have a feeling that the upgrades I've been getting has also affected my driver.

here is what shows up in the terminal:

webmiester@mobile-one-linux:~$ sudo lshw -C network
[sudo] password for webmiester: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:21:85:4d:11:28
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.5 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 22
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 12:ba:e9:57:68:12
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


-----------------

What do you guys think could be the problem?

---

