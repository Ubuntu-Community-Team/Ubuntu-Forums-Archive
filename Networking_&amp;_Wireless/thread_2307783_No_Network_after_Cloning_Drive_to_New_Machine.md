---
title: "No Network after Cloning Drive to New Machine"
date: 2015-12-28
forum: Networking &amp; Wireless
---

### Post by mcapaldo on 2015-12-28
I have a good working AMD 965 4 core CPU system with gigabit networking running fine, but its an older system and I just got all the components for a new fx-8350 8 core system.        I cloned the 4 core cpu drive, and it boots fine to the desktop in the new 8 core cpu system.  But the network does not work.  At 1st I thought the new MB and onboard NIC was bad, but I booted off a 14.02 LTS Live CD and network works fine on that.  so it has to be a network driver problem.       Oh I am using Ubuntu Desktop LTS 14.042 64 Bit.         Rather than doing a backup and re-installing the OS, reinstalling all my programs and doing a data restore (which I can do as I have a Ubuntu Server that I backup to weekly if I have to).    Is there a way to tell Ubuntu to figure out there is a new network controller and use that one?  I would be using the same video card Geforce 610 PCI-E 1GB DDR3.        Old system: AMD Quad Core 964 3.4GHz, Asrock Non USB3 or sata 6 Motherboard, 2 GB DDR3 1333MHz Ram, 320 GB Sata II HD, Sata DVD Rom, Geforce 610 PCI-E 1gb DDR3 Video Card.  **NOTE** I checked and fx-8350 was NOT on supported CPU list for this MB and it did not have usb3 or sata 6.        New System: AMD FX-8350 8 Core 4.0GHZ CPU, Gigabyte 970-D3SP Motherboard, 8 GB DDr3 1600MHz RAM, WD Blue Sata6 500 GB Drive, Sata DVD RW Drive.  (same video  card from old above system) Geforce 610 PCI-E 1gb DDR3 Video Card.

 **SOLVED SORT OF** Known Bug with Gigabyte 970a-d3sp motherboard.  Fix is to goto bios and ENABLE IOMMU.  Then unplug network cable, save and exit and re-plug NIC cable and then network works, BUT usb3 does not.  


run the following command: sudo gedit /etc/default/grub


Edit the empty quotes in this line to read: GRUB_CMDLINE_LINUX="iommu=soft"


save changes to grub and exit gedit and the terminal


Open up a new terminal with ctrl+alt+t 


run the following command: sudo update-grub


then exit the terminal using this command: exit


Restart your computer press delete to get back into the uefi


Disable iommu in bios, load optimized defaults and restart.

---

### Post by matt_symes on 2015-12-28
Hi

What release of Ubuntu do you have installed on the system ? I also take it that it's a desktop installation using Network Manager ?

To get the ball rolling, please post the output of these commands from the terminal.

```
lspci -nnk | egrep -iA2 "network|ethernet"
```

That's a capital A above.

```
ifconfig -a
```

```
nmcli dev
```

Kind regards

---

### Post by mcapaldo on 2015-12-28
Old 4 Core system,  ASRock M3A770DE Motherboard AMD 965 3.4GHZ CPU. 

```
lspci -nnk | egrep -iA2 "network|ethernet" 

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03) 	Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168] 	Kernel driver in use: r8169 
```

```
ifconfig -a 

eth0      Link encap:Ethernet  HWaddr 00:25:22:5d:b0:52             inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0           inet6 addr: fe80::225:22ff:fe5d:b052/64 Scope:Link           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1           RX packets:341072 errors:0 dropped:0 overruns:0 frame:0           TX packets:170213 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000            RX bytes:432386425 (432.3 MB)  TX bytes:18449697 (18.4 MB) 

lo        Link encap:Local Loopback             inet addr:127.0.0.1  Mask:255.0.0.0           inet6 addr: ::1/128 Scope:Host           UP LOOPBACK RUNNING  MTU:65536  Metric:1           RX packets:20542 errors:0 dropped:0 overruns:0 frame:0           TX packets:20542 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:0            RX bytes:1946737 (1.9 MB)  TX bytes:1946737 (1.9 MB) 

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00             BROADCAST MULTICAST  MTU:1500  Metric:1           RX packets:0 errors:0 dropped:0 overruns:0 frame:0           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
```

```
nmcli dev 

DEVICE     TYPE              STATE         
eth0       802-3-ethernet    connected
```

---

### Post by matt_symes on 2015-12-28
Hi

> **mcapaldo said:**
> Old 4 Core system,  ASRock M3A770DE Motherboard AMD 965 3.4GHZ CPU. 

We need the output of those commands from the computer where networking is not working, not from the computer where networking is working.

Kind regards

---

### Post by weatherman2 on 2015-12-28
Try this:

```

sudo rm -f /etc/udev/rules.d/70-persistent-net.rules

```

Reboot.

This should erase any memory of the old network card and re-assign "eth0" to the new one.  No doubt eth0 is set to be your default network connection.  (This exact problem has happened to me more than once after moving a drive to a system with a new network card.)

---

### Post by mcapaldo on 2015-12-29
Cloned fx-8350 PC Jpeg Attached.  I tried to use a document copy via USB and the old 4x core pc does not see the copied document on 2 different known good flash drives.  So thats another problem,

I did notice that the 8 core system uses ETH1.  Old 4x core system uses ETH0.

---

### Post by weatherman2 on 2015-12-29
Did you try erasing the udev rules file as suggested above so that the old network card isn't being reserved for eth0?

---

### Post by mcapaldo on 2015-12-29
yes still not working internet after reboot.  I was using static IP's so I changed to DHCP (which I know is working) and no luck.

So I re-formatgted the drive with 14.042 64 bit ubuntu desktop and still no internet.  changed network cable.  no good.

---

### Post by mcapaldo on 2015-12-29
So I went back to an old known good hd with working internet on this new 8 core system.  Ubuntu v10.10 and internet works.  using Kernel 2.6.35-32-generic and this drive is from a different 4x core  system

But fresh install of 14.042 64 bit does not work for internet.  

lspci -nnk | egrep -iA2 "network|ethernet"

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 0c)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
    Kernel driver in use: r8169

ifconfig -a

eth1      Link encap:Ethernet  HWaddr fc:aa:14:c5:02:3b  
          inet addr:192.168.0.110  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::feaa:14ff:fec5:23b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4421 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3219 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4405352 (4.4 MB)  TX bytes:452515 (452.5 KB)
          Interrupt:75 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:67 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5560 (5.5 KB)  TX bytes:5560 (5.5 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

nmcli dev

DEVICE     TYPE              STATE       
eth1       802-3-ethernet    connected

---

### Post by weatherman2 on 2015-12-29
Is that still static IP or are you using DHCP now?  Because the results above show you got an IP (192.168.0.110).

Can you ping anything? Try pinging 192.168.0.1 (should be your gateway).  If that works, try pinging 216.58.193.110 (Google).  If that works, maybe your real issue is a DNS issue (names) - try pinging google.com directly .

FYI, you can download/build the Realtek 8168 driver, because that's the network card you seem to have - it is common for the 8169 driver to be used by default.  I know I had to build the 8168 driver to fix another issue (with Wake-On LAN) on one motherboard, though in my case I still had working internet.  I don't know that building 8168 would fix any problem for you.

---

### Post by mcapaldo on 2015-12-29
I am using static IP address, I tried DHCP also no luck, except on that old 10.10 ubuntu drive.    Gigabyte DSP3 v2 MB has got that new UFEI Bios, would that have an effect on it?  I saw the 14.042 install disk was really scratched so I downloaded the 14.043 64 bit and installed that and same thing no network connect.    I ran ping 192.168.0.1 and it times out for a while then it starts working.  When I try to open [www.google.com](www.google.com) it can not connect.  and ping no longer works.  I tried new ram, different HD, new EVGA Power Supply.  Ran another network cable also.  Different port on gigabit switch.  Back of PC the NIC light is orange.    I went full green once then out then orange.

---

### Post by weatherman2 on 2015-12-29
You can try downloading the 8168 driver from Realtek then (presumably using your 10.10 boot or another OS to a flash drive):

[http://www.realtek.com.tw/Downloads/downloadsView.aspx?Conn=4&DownTypeID=3&GetDown=false&Langid=1&Level=5&PFid=5&PNid=13](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Conn=4&DownTypeID=3&GetDown=false&Langid=1&Level=5&PFid=5&PNid=13)

and try building it.  I just downloaded the latest and took a look.  There is a README file you can take a look at but you might not need to worry about much in there.  You can probably get away with just doing

```

sudo ./automake.sh

```

after you've untarred it and cd'd into the new directory that is created.

You may have to blacklist the r8169 module so it isn't loaded instead.

---

### Post by mcapaldo on 2015-12-29
Well I did a google search on the Gigabyte 970a-ds3p motherboard.  And it seems to be a known BUG.  The fix for now is 

run the following command: sudo gedit /etc/default/grub


Edit the empty quotes in this line to read: GRUB_CMDLINE_LINUX="iommu=soft"


save changes to grub and exit gedit and the terminal


Open up a new terminal with ctrl+alt+t 


run the following command: sudo update-grub


then exit the terminal using this command: exit


Restart your computer press delete to get back into the uefi


Disable iommu in bios, load optimized defaults and restart.

---

