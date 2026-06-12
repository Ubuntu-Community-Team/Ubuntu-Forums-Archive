---
title: "Asus P5Q Pro with Attansic gigabit nic won't work"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by Roderik on 2008-06-27
Ok, i bought myself a new computer, Asus P5Q Pro mobo with the new P45 chipset, quad core intel and 4 gb of memory.

All very nice, but for the network interface. No drivers are found for it (not in hardy 32bit, 64bit or opensuse 64bit)

I con't find out for sure what driver ineed to load. atl1 and atl2 don't work, but i'm just guessing. Tried everything i could find on the forum abount this netwerk card but nothing helps. 

Does anyone have an idea? All the information needed should be attached below 

```

roderik@tenedos:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: b0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0


roderik@tenedos:~$ lspci
00:00.0 Host bridge: Intel Corporation Eaglelake DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Eaglelake PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation ICH10 USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation ICH10 HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation ICH10 PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation ICH10 PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation ICH10 PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation ICH10 USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation ICH10 USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation ICH10 USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation ICH10 USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation ICH10 LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation ICH10 6 port SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation ICH10 SMBus Controller
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
02:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
05:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

roderik@tenedos:~$ sudo ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:772 errors:0 dropped:0 overruns:0 frame:0
          TX packets:772 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40296 (39.3 KB)  TX bytes:40296 (39.3 KB)

```

---

### Post by chrisccoulson on 2008-06-27
Thats a shame. I did a Google search for your chipset and Linux and didn't get that many relevant hits. I did find [this]("http://vip.asus.com/forum/view.aspx?board_id=1&model=P5Q&id=20080624021821000&page=1&SLanguage=en-us") though - it seems you're not alone!

Edit: And another discussion [here too]("http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/614001403931")

---

### Post by l_99 on 2008-06-28
It requires a driver called atl1e see: [http://www.gossamer-threads.com/lists/linux/kernel/938155]("http://www.gossamer-threads.com/lists/linux/kernel/938155")

#define PCI_DEVICE_ID_ATTANSIC_L1E 0x1026 corresponds to the pci id...

---

### Post by chili555 on 2008-06-28
See post #7 here: [http://ubuntuforums.org/showthread.php?t=770173](http://ubuntuforums.org/showthread.php?t=770173)

---

### Post by johann_p on 2008-06-30
This looks scary. I had planned to buy a P5Q but manually messing with drivers that do not come with the distribution or even compiling them is not something I want to do.

Does this mean P5Q is not supported out of the box with Hardy?

---

### Post by Roderik on 2008-06-30
i bought a basic 10/100 nic for €9 :) you can't compile the driver, if you can't apt-get...

---

### Post by johann_p on 2008-06-30
Hmm as long as I am not short on slots that could be a solution. The unsupported driver wont do any harm though?

Is this the only known problem with the P5Q and Ubuntu?

---

### Post by Roderik on 2008-06-30
all the rest works great out of the box (although i haven't tested the e-sata etc)

---

### Post by l_99 on 2008-06-30
Maybe be you should buy the next model up P5Q-E (?) which uses Marvell ethernet controllers. 

I've raised a bug with Unbuntu for the missing atl1e driver,

---

### Post by pnuts2 on 2008-07-03
I've bought the same board as well and with the same LAN problem. Moreover, I couldn't get my nVidia GeForce 7800 GT to work either. Every time when I installed the restricted driver, the system rebooted to "low graphics mode". I did a lot of search (even tried the official nVidia driver) and some pointed out that the driver might conflict with Intel ICH10R, which is the south bridge used on this board. Has anyone successfully got the VGA card working on this board? Please shed some light......

I'm using Vista atm and that is how frustrated I'm...

---

### Post by Roderik on 2008-07-03
I only run an old 6600, but no problems for me on the graphics end. (not even in dual screen 1920x1600 + 1600x1200)

---

### Post by pnuts2 on 2008-07-03
are you running Hardy's restricted driver or nVidia's official driver from their website?

The thing is I can see xorg config file saying it is using nVidia driver, but for some reasons, the system rebooted to low graphics mode everytime...

---

### Post by leech on 2008-07-05
I'm running the P5Q as well, and have the atl1e installed as well (though I'm running Debian Sid).  

Everything is currently working on this board except I'm having issues with my DVD burner (though I think I have resolved those, the CD-R's I bought are just crap, it burned fine at 4x, but at 38x it craps out (they are rated 52x).

The other problem I have is the IDE controller isn't showing my DVD-ROM drive...

As far as the nVidia driver not working, it's working great here with my 9800 GTX.  So maybe it's an Ubuntu kernel issue.

Leech

---

### Post by a9db0 on 2008-07-31
If you have a P5Q, are your SATA disks running at 1.5GB or 3.0GB?  Because while I've got no issues with my DVD, I can't get the SATA drives on the ICH10R to go above SATA I speed.

---

### Post by Roderik on 2008-08-01
Is there a tool to check this? hdparm?

---

### Post by BigTK41 on 2008-08-11
Hi Everyone. I joined this forum after reading dozens of messages regarding the P5Q Pro board and the Atheros Gigabit Lan not working. I just finished building my pc with this board and I had the same trouble, no internet. I have tried everything I know to no avail. I started my pc this morning and I noticed I had not plugged the Lan cable:) in, with the pc turned on I plugged it back in and it immediately connected me to the Internet. Microsoft updated my o/s Vista with SP1 and when it rebooted I had lost my internet connection again. I unplugged the lan cable, rebooted my pc plugged my cable back in and I am on the net again.I know this sounds weird but it works for me and I know it's a pain in the a..e but it will do me until a fix comes along to sort it out. Give it a try you have nothing to lose and it may work for you.:)

Vista Ultimate
P5Q Pro Board
Quad Q6600 CPU
2Gig Corsair DDR2 800
MSI N9600GSO T2D768 Graphics
4x500Gig WD HDD's
Corsair 620W PSU
Asus Silent Knight CPU Cooler
D-Link G604T ADSL router

---

