---
title: "Wifi problem"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Kaia on 2009-01-27
Hi, I'm new here and I hope you can help me with my problem. Like many people, I can't get the wifi to work, since i installed Ubuntu. I have an [HP Pavilion dv2000]("http://asia.cnet.com/reviews/notebooks/0,39050490,39259551p,00.htm"). I did the lspci thing, and this is the result:
```
kaia@kaia-portatil:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
```

And lshw -C network:
```
kaia@kaia-portatil:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: BCM4310 UART
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@01:00.0
       logical name: eth1
       version: 01
       serial: 00:14:a5:d8:e6:15
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-17-generic latency=0 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:c3000000-c3003fff irq:20
```

Aaaand iwconfig:

```
kaia@kaia-portatil:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Network settnings: 
```
kaia@kaia-portatil:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
kaia@kaia-portatil:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

Now, the history. I have a button, to turn on and off the wifi on the computer, but either way, the light is always red that indicates it's not activated. 
When I had windows, a window popped up that said the I had to go to BIOS, and activate the driver, but in BIOS I couldn't see anything to activate the driver. 

I think the solution is to activate the driver, but I don't know how to do it :(

And by the way, I have windows in one partition, and ubuntu in another one, can i "transfer" f.e. photos from ubuntu to windows and viceversa?

If you need more info, let me know ;)

---

### Post by beyboo on 2009-01-27
Try this link.

[http://ubuntuforums.org/showthread.php?t=1010650](http://ubuntuforums.org/showthread.php?t=1010650)

I know of a Dell user who has a problem with his broadcomm wireless card. This link made the thing work smooth !!

---

### Post by beyboo on 2009-01-27
> **Kaia said:**
> 
And by the way, I have windows in one partition, and ubuntu in another one, can i "transfer" f.e. photos from ubuntu to windows and viceversa?

If you need more info, let me know ;)

What is the error you get when u transfer ? Could be a permission issue.

---

### Post by Kaia on 2009-01-27
> **beyboo said:**
> What is the error you get when u transfer ? Could be a permission issue.

I never have done it, 'cause I don't know how it's done...

---

### Post by Ayuthia on 2009-01-27
If you have a working internet connection in Ubuntu, please go into Synaptic and run the updates.  Once it is updated, there should be an option in System->Administration->Restricted Drivers (or Hardware Drivers) for a Broadcom STA module.  You will need to activate that and it should start working (with a possible reboot).

EDIT:  From your lspci info, it looks like you are using Hardy 8.04 (It shows your card as a 4310 instead of 4312).  The module for your wireless is introduced in 8.04.1.  However, if you update your system and reboot, you should get the option to install the wireless module.

---

### Post by Kaia on 2009-01-27
> **Ayuthia said:**
> If you have a working internet connection in Ubuntu, please go into Synaptic and run the updates.  Once it is updated, there should be an option in System->Administration->Restricted Drivers (or Hardware Drivers) for a Broadcom STA module.  You will need to activate that and it should start working (with a possible reboot).

EDIT:  From your lspci info, it looks like you are using Hardy 8.04 (It shows your card as a 4310 instead of 4312).  The module for your wireless is introduced in 8.04.1.  However, if you update your system and reboot, you should get the option to install the wireless module.

Well, I just updated 233 thing, so in synaptic i didn't see anything. In restricted drivers nothing...

So you say I have to get a newer version of ubuntu?

---

### Post by stchman on 2009-01-27
You have a dreaded Broadcom wireless card.  Easiest way to get that card to work is to hook your laptop up to a wired connection and install ndisgtk.

```

sudo apt-get install ndisgtk

```

Then install the Windows wireless drivers that came with your laptop.  There will be a .inf file in the archive.

Launch ndisgtk by doing System--->Administration--->Wireless

then navigate to the .inf file.

This should work.

---

### Post by Kaia on 2009-01-27
> **stchman said:**
> You have a dreaded Broadcom wireless card.  Easiest way to get that card to work is to hook your laptop up to a wired connection and install ndisgtk.

```

sudo apt-get install ndisgtk

```

Then install the Windows wireless drivers that came with your laptop.  There will be a .inf file in the archive.

Launch ndisgtk by doing System--->Administration--->Wireless

then navigate to the .inf file.

This should work.

```
kaia@kaia-portatil:~$ sudo apt-get install ndisgtk
Password:
E: No s'ha pogut blocar /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
kaia@kaia-portatil:~$ sudo apt-get install ndisgtk
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
E: No s'ha pogut trobar el paquet ndisgtk

```

The second error is that he cant find the "pack ndisgtk" :(

---

### Post by stchman on 2009-01-27
> **Kaia said:**
> ```
kaia@kaia-portatil:~$ sudo apt-get install ndisgtk
Password:
E: No s'ha pogut blocar /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
kaia@kaia-portatil:~$ sudo apt-get install ndisgtk
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
E: No s'ha pogut trobar el paquet ndisgtk

```

The second error is that he cant find the "pack ndisgtk" :(

Looks like you have Synaptic open.  Close Synaptic.  Also make sure you have all the repositories enabled (main, universe, multiverse, and restricted).  Do you have a wired internet connection hooked up?

[http://packages.ubuntu.com/intrepid/ndisgtk](http://packages.ubuntu.com/intrepid/ndisgtk)

---

### Post by Kaia on 2009-01-27
> **stchman said:**
> Looks like you have Synaptic open.  Close Synaptic.  Also make sure you have all the repositories enabled (main, universe, multiverse, and restricted).  Do you have a wired internet connection hooked up?

[http://packages.ubuntu.com/intrepid/ndisgtk](http://packages.ubuntu.com/intrepid/ndisgtk)

[IMG]http://img84.imageshack.us/img84/5899/erroria1.png[/IMG] This happens everytime i try to install something...

Now i'm updating to ubuntu 8.10, let's see if that makes things better. [-o<

---

### Post by Kaia on 2009-01-27
By the way. How can I install ubuntu 8.10 that i just downloaded? This one i got from a cd..

---

### Post by clive littlewood on 2009-01-27
Hi

The file you dowloaded should be an .iso file

Burn this file to a CD as an iso NOT data file.

This CD will then be both a live CD and install CD

Boot from the CD as live and you can then see if your WiFi and everything else is detected before you install

Hope this helps

Clive

---

