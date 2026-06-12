---
title: "Network Manager - permission denied!"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by brasini on 2011-03-23
Wifi hasn't been working for a while and I haven't found anything on forums yet that helped solve it. Help and suggestions appreciated (please and thank you).

Right-clicking the connection manager applet won't let me select 'enable networking' because that option is shaded. 

The other Network Manager icon has turned into what looks like a light bulb after I enabled Network Manager (from System>Start Applications>Network Manager). Scrolling over this light bulb tells me that Connection Manager daemon is not running. (How do I get it to run?) Right-clicking opens a connection preferences window with zero devices showing. 

I've also asked for /var/lib/NetworkManager/NetworkManager.state and got:
bash  /var/lib/NetworkManager/NetworkManager.state: permission denied   

It used to work fine until I did I don't know what to it. Thanks.

---

### Post by Hippytaff on 2011-03-23
What's the output of```
lspci
``````
rfkill list
``` ```
iwconfig
``` and```
lshw -C network
```
Edit -> also has it stopped working since an update?

---

### Post by brasini on 2011-03-23
If I'm honest it stopped working after I did a selective update - I de-selected some things on the update manager list for no special reason. I don't know why I did that. 

Thanks for the super quick reply.

**~$ lspci**
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

**~$ rfkill list**
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

christalla@christalla-Vostro-1500:**~$ iwconfig**
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

**~$ lshw -C network**
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:14:a5:ab:5e:6d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:de:7a:09
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.2 latency=64 multicast=yes
       resources: irq:17 memory:fe5fe000-fe5fffff

---

### Post by Hippytaff on 2011-03-23
ok...before we go any further does doing```
 sudo apt-get update && sudo apt-get upgrade
``` fix anything.

if not can I see the output of```
lsmod | grep 4401
```

---

### Post by brasini on 2011-03-23
Ok, 
 sudo apt-get update && sudo apt-get upgradegot a Flash Plugin installed. 

Is this a command that tells you what the system needs / is missing? 

Also, what does:
lsmod | grep 4401
do? When should it be used?
Thank you

---

### Post by Hippytaff on 2011-03-23
Thats just to update the system...software...security etc.

the lsmod thing shows what drivers are installed...we are looking for your BCM4401 driver as that is your wireless chipset. The grep bit menas that only results matching 4401 - I ballsed up a bit though, we should be looking for 4311 so when you run that change 4401 to 4311 :?

---

### Post by brasini on 2011-03-23
No worries. 4311 doesn't give an output. Just goes back to prompt. 

Meanwhile, I did a restart and the light bulb icon has turned back into something else - it looks like an ethernet image with a red line going through it though NM is still enabled in start up applications.

---

### Post by Hippytaff on 2011-03-23
I was going to suggest installing the propriety driver but you have got there already it seems :-)

Any luck with that?

---

### Post by brasini on 2011-03-23
No. Soon after I messed up and lost wifi I saw that the driver was deactivated, I think it also went completely missing at one point, but no it doesn't make a difference once I got it back and activated. I've also tried uninstalling and reinstalling Network Manager from Syanptic, no luck there either. But I wonder why I would be denied permission to /var/lib/NetworkManager/NetworkManager.state ?

---

### Post by Hippytaff on 2011-03-23
try this ```
 sudo cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by brasini on 2011-03-23
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

True, but when I right click NM applet, 'Enable Networking' is still shaded/unselectable.

---

### Post by Hippytaff on 2011-03-23
Just to clarify, this is stopping you getting online (connecting) or it's just greyed out?

---

### Post by brasini on 2011-03-23
Greyed out. From what I saw on threads, forgetting to enable this option was a common factor on people not being able to get online so I've become obsessed with ungreying it. (Scrolling over the NM icon shows that 'Networking disabled')

---

### Post by Hippytaff on 2011-03-23
haha - I completely misunderstood, sorry..I was diagnosing a malfunctioning wireless card lol.

---

### Post by brasini on 2011-03-23
So sorry to keep firing questions, just got one more about the 'Connection Manager daemon not running' issue. Do you know how/where I can find out about this?

I've had a browse at the blog, it's really good, accessible stuff. Fab resource. Many thanks.

---

### Post by Hippytaff on 2011-03-23
You are too kind

[This]("http://manpages.ubuntu.com/manpages/maverick/man8/NetworkManager.8.html") might be worth a read

---

### Post by brasini on 2011-03-23
Thanks for the manual, I will go through it patiently another time. 
For now I'm content with the embarrassing lesson of having to re-learn that sudo temporarily gives you permission to do stuff. 

As for the blog, not flattery - please don't underrate the value of accessible step-by-step guides for super slow learners like myself. 

Ta

---

### Post by Hippytaff on 2011-03-24
I'm glad you found it useful - it gets updated farily infrequently but I'll probably be doing a wireless troubleshooting post soon.

Happy ubuntuing :-)

---

### Post by brasini on 2011-04-10
Partially solved this. I reinstalled the indicator applet that disappeared. I also removed connman from synaptic package manager - there might have been a few conflicts there.  

/var/lib/NetworkManager/NetworkManager.state still returns: NetworkingEnabled=true
although mousing over the network manager shows 'Networking disabled'. But that doesn't worry me too much now as I can finally use wifi which is what I wanted.

Thanks for all the help Hippytaff.

---

### Post by Hippytaff on 2011-04-10
Glad you managed to sort it, sorry I couldn't be of more help :-)

---

