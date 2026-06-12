---
title: "internet connected but wireless does not work"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by marinaga on 2008-06-16
I am completely new to all this and took the linux plung. I hope you all can help.
 
i am running 6.06 dapper

I have no clue what driver i need. 

this is what i get from lspci

agathamarin@agathamarin-laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
0000:00:1f.2 0106: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=AHCI (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:02:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)0000:05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:05:05.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:05:05.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)0000:05:08.0 Ethernet controller: Intel Corporation: Unknown device 1092 (rev 02)


please help.

also having problems with screen resolution and external speakers

---

### Post by pytheas22 on 2008-06-16
First of all, is there a reason you're using such an old release?  If it's not too difficult, I'd recommend downloading the latest version of Ubuntu, 8.04.  There's a good chance that your wireless will "just work" in a more up-to-date version.

If you really need to use 6.06, I'll still do my best to help.  Please post the output of:

lshw -C Network
iwconfig

to get a better idea of what's going on.  Also do you have any idea what the name of your wireless card is?  lspci isn't providing as much information as it should.

---

### Post by marinaga on 2008-06-16
i've been trying to upgrade to hardy but that is proving difficult as well :( 
first tried to just get an update box to come up, then tried alternate cd, and now trying just to download to desktop? we'll see.

I wish i new wireless name. It is a built in wireless on hp dv6226us on linksys wrt5G router hope that helps. 

agathamarin@agathamarin-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth1
       version: 02
       serial: 00:19:d2:0c:8d:1e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 multicast=yes wireless=unassociated
       resources: iomemory:d6000000-d6000fff irq:177
  *-network
       description: Ethernet interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@05:08.0
       logical name: eth0
       version: 02
       serial: 00:16:36:cb:c4:13
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 ip=192.168.1.103 multicast=yes
       resources: iomemory:d8000000-d8000fff ioport:4000-403f irq:50


agathamarin@agathamarin-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"PANAMA"
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:19186   Missed beacon:0

sit0      no wireless extensions.

---

### Post by pytheas22 on 2008-06-16
Thanks for the information.

If you have the ability to burn a CD and broadband Internet, you can download the newest version of Ubuntu from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) .  It will not take more than a few hours, and on a faster connection it could be as quick as a few minutes.  Upgrading over the Internet to 8.04 is going to take much longer and you're likely to run into problems.  Then just wipe out Dapper and do a fresh install (since you're new to Linux, I'm assuming you don't have any reason to need to keep your current information).

Otherwise I'm not really sure what to do.  The information you provide indicates that your wireless card has an Intel chipset, but it's not any more specific than that, so I don't know which driver to tell you to use.  I've never seen lspci output before that doesn't say exactly which type of chipset is in a card.

So please keep on trying to upgrade to a newer Ubuntu and post back.  If you really can't get upgraded we'll figure something out, but I think it would be much easier to use a newer version of the operating system than to try to figure this out in the dark in Dapper.  Intel wireless cards in general have great support, so I'd be surprised if yours doesn't just work in Hardy anyway.

---

### Post by marinaga on 2008-06-17
i got hardy on my computer finallyyyyyyyy. turns out i had a bad batch of cd's that i was trying to burn the alternate iso to. I think that solves those problems. Thanks so much for responding.

---

### Post by pytheas22 on 2008-06-17
Glad to hear you finally got Hardy installed, where I hope the wireless will work better.  Have fun with Ubuntu!  And if you still have the same issues with resolution and speakers in Hardy, feel free to post...

---

