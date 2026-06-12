---
title: "cant load network driver"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by ggumas on 2007-09-21
[FONT=DejaVu Sans, sans-serif][SIZE=2]**I am trying to load Ububtu 7.04 from a live disc on a HP6510 notebook with a vista operating system.**[/SIZE][/FONT]
 [FONT=DejaVu Sans, sans-serif][SIZE=2]**When loading the system fails to find thr Xserver. When I attempt to load a driver with an  apt-get command I find that I have no network connection. **[/SIZE][/FONT] 
 [FONT=DejaVu Sans, sans-serif][SIZE=2]**The network connection however does work on the 6510 when I amusing vista.**[/SIZE][/FONT]
 [FONT=DejaVu Sans, sans-serif][SIZE=2]**In an attempt to track down my problem I ran the the following commands**[/SIZE][/FONT]
 

 

 [FONT=DejaVu Sans, sans-serif][SIZE=2]**OUTPUT FROM   [FONT=DejaVu Sans, sans-serif][SIZE=2] lshw -C network[/SIZE][/FONT]**[/SIZE][/FONT]
         [FONT=DejaVu Sans, sans-serif][SIZE=2]***-network**[/SIZE][/FONT]
               [FONT=DejaVu Sans, sans-serif][SIZE=2]**description Erhernet interface**[/SIZE][/FONT]
               [FONT=DejaVu Sans, sans-serif][SIZE=2]**product: NetLink BCM5787M Gigabit Ethernet PCI Express**[/SIZE][/FONT]
               [FONT=DejaVu Sans, sans-serif][SIZE=2]**vendor: Broadcom Corporation**[/SIZE][/FONT]
                [FONT=DejaVu Sans, sans-serif][SIZE=2]**physical id:0**[/SIZE][/FONT]
                [FONT=DejaVu Sans, sans-serif][SIZE=2]**bus info: [EMAIL="pci@18"]pci@18[/EMAIL]:00.0**[/SIZE][/FONT]
                [FONT=DejaVu Sans, sans-serif][SIZE=2]**logical name: eth0**[/SIZE][/FONT]
                 [FONT=DejaVu Sans, sans-serif][SIZE=2]**version:02**[/SIZE][/FONT]
                [FONT=DejaVu Sans, sans-serif][SIZE=2]**serial: 00:17:a4:e2:da:39**[/SIZE][/FONT]
                [FONT=DejaVu Sans, sans-serif][SIZE=2]**capacity: 1GB/s**[/SIZE][/FONT]
                [FONT=DejaVu Sans, sans-serif][SIZE=2]**width: 64 bits**[/SIZE][/FONT]
                [FONT=DejaVu Sans, sans-serif][SIZE=2]**clock: 33MHZ**[/SIZE][/FONT]
                [FONT=DejaVu Sans, sans-serif][SIZE=2]**capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation=on broadcast=yes driver= tg3 driverversion= 3.72 latency =0 link=no multicast=yes port=twisted pair resources: iomemory:e4000000-e400ffff irq:18**[/SIZE][/FONT]
 [FONT=DejaVu Sans, sans-serif][SIZE=2]**####**[/SIZE][/FONT]
 

 [FONT=DejaVu Sans, sans-serif][SIZE=2]**OUTPUT FROM   [FONT=DejaVu Sans, sans-serif][SIZE=2]etc$ cat modules [/SIZE][/FONT]**[/SIZE][/FONT] 
 [FONT=DejaVu Sans, sans-serif][SIZE=2]**==>**[/SIZE][/FONT]
 [FONT=DejaVu Sans, sans-serif][SIZE=2]**fuse**[/SIZE][/FONT]
 [FONT=DejaVu Sans, sans-serif][SIZE=2]**#####**[/SIZE][/FONT]
 

 [FONT=DejaVu Sans, sans-serif][SIZE=2]**OUTPUT FROM   lspci**[/SIZE][/FONT]
    
        [FONT=DejaVu Sans, sans-serif][SIZE=2]**00:1e.0 PCI Bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)**[/SIZE][/FONT]
        [FONT=DejaVu Sans, sans-serif][SIZE=2]**00:1f.0  ISA Bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)**[/SIZE][/FONT]
        [FONT=DejaVu Sans, sans-serif][SIZE=2]**00:1f.1  IDE Interface: Intel Corporation Mobile IDE Controller (rev 03)**[/SIZE][/FONT]
        [FONT=DejaVu Sans, sans-serif][SIZE=2]**00:1f.2  SATA controller: Intel Corporation Mobile SATA AHCI controller (rev 03)**[/SIZE][/FONT]
        [FONT=DejaVu Sans, sans-serif][SIZE=2]**02:04.0  Cardbus bridge: Ricoh Co Ltd RD5c476 II (rev b6) **[/SIZE][/FONT] 
        [FONT=DejaVu Sans, sans-serif][SIZE=2]**02:04.1  Firewire (IEEE 1394) :Ricoh Co Ltd Unknown device 0832  (rev 02)**[/SIZE][/FONT]
        [FONT=DejaVu Sans, sans-serif][SIZE=2]**10:00.0 Network controller: Intel corporation PRO/Wireless 3945ABG            Network Connection (rev 02)**[/SIZE][/FONT]
        [FONT=DejaVu Sans, sans-serif][SIZE=2]**18:00:0 Ethernet controller : Broadcom corporation NetLink BCM5787M Gigabyte Ethernet PCI Express (rev 02)**[/SIZE][/FONT]
 

 

 [FONT=DejaVu Sans, sans-serif][SIZE=2]**I cant quite decipher them but it seems that the loaded kernel recognized the presence of my Network controller, and Ethernet controller,(see lscpi output) but failed to load them (see (cat etc/modules.) If this is the case how do I go correcting this. Do I modify my etc/module file?. If so how do I go about doing this (remembering that I do not have a  xserver ?**[/SIZE][/FONT]
 

 

 [FONT=DejaVu Sans, sans-serif][SIZE=2]**George G**[/SIZE][/FONT]

---

### Post by noob12 on 2007-09-22
Your card is detected and the tg3 driver has claimed the device.  It thinks the link is down.  This can be due to a number of issues.

Note that cat /etc/modules doesn't show you what's loaded, it specifies things you want to be loaded explicitly that wouldn't otherwise be loaded automatically.

When you booted the LiveCD, it wasn't able to start the graphical display?   I don't see your graphics controller in your lspci output.  This could be a sign of  significant PCI routing problems at boot, which could be contributing to this problem.

It might help if you can manage to post the output of the **dmesg** command after your boot.

---

### Post by ggumas on 2007-09-24
noob12, I failed to give the full story concerning my problem.
I should have included the following:
         When my live CD begins to load, it soon locks up with the message
            "can;t access tty job control off"
         and I am unable to get to a prompt'
In an attempt to fix this problem, I reboot the Live CD. and when the ubuntu logo comes up, I enter F6 and the delete "quiet" and "splash" replacing this with all_generic_ide.
After which the live Cd runs for a while until it comes up with the can't find xserver message.
   As for running dmesg, I tried this but the message was too long to post, 
I compared the output of dmessg to that from an operating Ubuntu on another computer, hoping this would be helpful, but it wasn;t.
Any suggestions would be helpful.

George G
  .

---

### Post by noob12 on 2007-09-25
It sounds like you've got some fundamental issues at boot that are affecting several devices on the motherboard; it's not just a networking issue.

You might try posting to the General Help forum or the Installation & Upgrades forum.

You could try booting with some of these boot flags and seeing if things improve at all:
**pci=noacpi** or **acpi=off** . These are just blind guesses though.

---

