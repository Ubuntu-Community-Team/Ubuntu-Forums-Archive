---
title: "Ubuntu 16.04 has slower Ethernet performance than 12.04 on same equipment"
date: 2016-12-01
forum: Networking &amp; Wireless
---

### Post by wglabs27 on 2016-12-01
I have a multiple OS/Boot machine that runs Windows 7 and Linux on separate dedicated disks. I've just upgraded my old Ubuntu/Gnome 12.04 LTS with Ubuntu/Gnome 16.04 LTS. I wiped the drive clean to install a fresh copy of16.04 LTS. With the older 12.04, I ran the SMB Client suite and was able to attain wired network transfer speeds to/from an old Windows 2003 server of around 30 Mbytes/second. My network is total Gigabit everywhere.

I have used the stock installation of 16.04 LTS--no SMB client suite. I'm able to log on to the Windows 2003 server using the "Connect to Server" option from going to Places:Computer: Connect to Server; it's very convenient, and I can create a bookmark to log on and mount the Windows network share. I am using a fixed IP address as previously with 12.04. 

The problem is that the maximum transfer speed I'm getting is a little over 4.2 Mbytes/second. Please note that I have made no changes to hardware--same machine, same Network adapter (Realtek RTL8111 family) on motherboard, same wiring. I've increased the MTU setting in the Network Configuration to 9000 and have turned off IPv6 as it is not used here. Still no improvement.

Incidentally, running Windows 7 with the same hardware gives me transfer speeds of 30 Mbytes/s or better--just as with the old Ubuntu 12.04.

What am I missing? Do I need to install the SMB Suite (with SMB4K) and remove what came in 16.04? Am I missing some configuration changes in files. I'm familiar with the older SMB client suite, but I'm not at all clear what's being used in 16.04. BTW: Ubuntu 16.04 is slick, and performs much better than the older 12.04 on my Intel QuadCore processor and 16 G of RAM. Hats off to everyone!

Thanks for any help!

---

### Post by TheFu on 2016-12-02
Welcome to the forums.

Can't tell what the issue is based on the data provided.

Some jumbo frame support isn't quite standard. Try a smaller frame size. All systems should be set to the same value, less than 9000. Try 8960 to be compatible with all HW limitations. All systems means servers, desktops, laptops, routers, switches ... anything that isn't set to 1500.
Check for the correct rtl driver for your system. There are different versions and you'll want to search for the exact, specific, driver for the card. Be specific about the letter at the end.  **sudo lshw -C network** will show this version and the exact driver used.
Test other protocols instead of SMB. On GigE hardware, you should be getting 920Mbps - try iperf.  With overhead, transfers with CIFS should be 65+MB/s, at least until RAM buffers are full.
Check that the switch/router ports are fine. Sometimes they fail.
Check that the cables used are fine. Sometimes the connectors or sharp turns make cables flaky.
Can all systems ping each other and themselves by the names you use? How is name resolution happening?

Sometimes it is the dumb things.  30MB/s is kinda slow, BTW, unless the storage is USB2.  On GigG networks, with fast disks, people get 100+Mbps CIFS xfers.

Never heard of or used "SMB Suite."

I always avoid realtek stuff. The drivers for it are never as solid/fast as those for Intel PRO/1000 NICs.  For $25, you can get an Intel NIC and full speed transfers will use 10x CPU.  Just sayin'.

Also, I've seen issues with jumbo frames breaking things that didn't make sense to me - time/NTP with Windows clients.  Never figured out why. Put everything back to normal, defaults (1500) and things have been relatively fast and problem free.

---

### Post by wglabs27 on 2016-12-02
Thanks so much for your response.

I tried changing the MTU to 8960 and back to 1500--still the same average speed of 4.2 MBytes/s. Yes 30-40 Mbytes/second is kinda slow for a Windows server by modern hardware standards, but this is vintage with a Pentium 4 processor and SATA drives connected through the PCI bus. Not lightning fast, but adequate for moving large graphics files back and forth or for opening a 200-Mbyte graphic file in GIMP. 

I can live with a couple of seconds for a 200-Mbyte file to open, but not the better part of a minute. What's weird is that using **Ubuntu 12.04 LTS on this very same PC** **did not slow the transfer speed down** to 4.2 Mbytes/s, so it is something with the configuration of **16.04 LTS out-of-the-box** that is **not matching the performance of 12.04 on this very same PC**--no changes in hardware including switches, cabling or whatever. Keep in mind that Windows 7 on this same PC is giving me 30+ Mbyte/second transfer speed (just like when I was running Ubuntu 12.04 on this box) to/from the old Windows 2003 Server.

SMB Suite refers to the old Samba suite, which included SMB4K on the front end with smbclient, etc.

Incidentally, I use the Intel-based 1 G-bit card that you are referring to on the Windows 2003 server. But this Ethernet interface is on the motherboard, and it had not given me any slowdowns when I ran Ubuntu 12.04 LTS.  So my final question is: If it worked just fine with Ubuntu 12.04 LTS, why don't I get the same results (or better) on 16.04 LTS when installing it as a fresh installation (with all updates)? If anything, I would have expected the drivers to be more up-to-date as this mother board is 4-6 years old. 

Here's the dump from lshw -C network:
*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 06
       serial: b8:97:5a:14:fa:34
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.0.21 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:27 ioport:c000(size=256) memory:f2104000-f2104fff memory:f2100000-f2103fff

---

### Post by TheFu on 2016-12-02
Have you tried the correct driver?  Currently using driver=r8169, but need a RTL8111/8168/8411.  Don't know how that happened. Could be related to all the systemd ethernet naming "fixes"?  

[https://askubuntu.com/questions/770368/realtek-ethernet-driver-error-ubuntu-16-04](https://askubuntu.com/questions/770368/realtek-ethernet-driver-error-ubuntu-16-04) says to **sudo apt-get install r8168-dkms** It didn't work for everyone, however.

---

### Post by wglabs27 on 2016-12-02
I will give this a try and let you know.
TNX!
Wayne

---

### Post by wglabs27 on 2016-12-02
Thanks for your suggestion. OK. I ran the driver install, and it installed successfully; I rebooted and tried MTU settings of 2048, 4096 and 8192.  See the report below indicating that it installed. I'm not seeing any speed degradation, but if there is an improvement, it might be slight--about 2%. I'm getting about 4.5 MBytyes per second--same equipment on Windows 7 about 20- 30 Mbytes/second.  I'm open to any other ideas. As I mentioned, this was a clean install from the Ubuntu disk plus updates. Here's the dump on the network card showing the "updated" driver you guggested
Again, thanks so much for your efforts; I've been an Ubuntu User for at least 10 years; first time, I've really worked with the community.-------------------------------------
*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 06
       serial: b8:97:5a:14:fa:34
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.041.00-NAPI duplex=full ip=192.168.0.21 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:27 ioport:c000(size=256) memory:f2104000-f2104fff memory:f2100000-f2103fff

---

### Post by TheFu on 2016-12-02
Ok, we don't know the root cause. Can you please perform (AND report results) from my other questions above?  Is this just a CIFS issue or are all other protocols having problems?  iperf, please.  For now, forget about jumbo frames too. Go back to the default, 1500.

---

