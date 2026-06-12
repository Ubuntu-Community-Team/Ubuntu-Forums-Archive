---
title: "Ubuntu 8.10 - vs - Bigpond Wireless."
date: 2008-12-08
forum: New to Ubuntu
---

### Post by lukehappy on 2008-12-08
Hi, I am having trouble connecting to the internet through my wireless device.

I have Ubuntu 8.10 desktop i386, dual booting with vista on a HP Pavilion dv9700 Notebook PC. Before I spend many a late night figuring out Ubuntu I want to get it hooked up to the internet with my Wireless Broadband 7.2 USB Mobile Card (ZTE MF636BP) 
Model:MF636, that runs on the Bigpond(Australia) Next G Network. I have installed ndiswrapper-utils from the cd but I have no idea how to use it.

Thankyou for your consideration of my problem.

---

### Post by bumanie on 2008-12-08
To use ndiswrapper, you need to find the .inf file from the windows driver for the card you have. Also if you install ndisgtk, it is a GUI front end to ndiswrapper and makes the task of installing the .inf much easier. But you need to find the .inf somewhere - it should be one the cd you got from telstra in the driver section. If you can't find the .inf file, you will have to ascertain the chipset of the card and try to find an .inf for that chipset. To find this try lspci in terminal.Post the output if you can't pick out the chipset. It is likely that telstra remarket a card with a common chipset.

---

### Post by lukehappy on 2008-12-08
Thankyou Bumanie, Unfortunatly I had to reboot Vista to get back here.

I found ZTEusbmodem.ini was the driver I then found that there were 64 and 32 bit versions for both Vista and Wnet. but when I went to get them from Vista from within Ubuntu I couldnt tell which was which so just got all four to try.

After installing ndisgtk_0.8.4-1_i386.deb I couldnt find it in applications but I did find an application called 'Wireless Network Drivers', so assumed this was what I was looking for.

I located the drivers for it but it rejected them all with the message 'could not find a network configuration tool'
-Because all four had the same name I had to prepend 1_ to the file, would that be a problem? I went back to try without the prepend but could not find the desktop from within the 'Wireless Network Drivers' program anymore.(I just got lost :')

other mucking around in terminal resulted with a message'su-to-root not installed'

Other Notes: 
-My Modem does not show up in network connections or on computer.
-The SD card in the modem does not show up.
-A USB mouse does work.
-Went into Windows and told the network adapter to not turn off on shut down and took it off the powersaver power plan.
-Other Folders that are found in the wireless driver tree, Maxon, Option, Sierra, and ZTE(the one Vista was using).

---

### Post by bumanie on 2008-12-08
Sorry forgot to say to start ndisgtk, go to terminal and type > sudo ndisgtkThis will start the gui. Also I am sure that ndis wrapper needs a .inf to work, don't think it will work with a .ini - but not 100% sure on that. Have you tried hardware drivers? Go to System --> Administration --> Hardware drivers, if the card is recognised by ubuntu, click the box to enable it and the correct driver will be downloaded. (I think that must be where you were before getting lost).

---

### Post by lukehappy on 2008-12-08
I am using .inf not ini, sorry that was a mistake.
Hardware drivers only finds 2 Nvida Drivers, I tryed to install the one that says recomended, it came back with an installation activated but in the main window still said not activated, so i dont know. My USB Modem has a slot for a SD memory card, Vista can find the SD Card in 'my computer' but not the wireless device. Ubuntu in 'computer' can not find the modem or the SD card.

---

### Post by 3rdalbum on 2008-12-08
To the people offering help:

The original poster is talking about wireless broadband, not wireless networking. They're talking about the type of broadband that connects to the mobile phone network while they're out and about, not the type of wireless that connects their computers to a router.

I haven't heard of Ndiswrapper being used for wireless broadband drivers; I could be wrong but are you sure you're not getting your wires (or wirelesses) crossed?

---

### Post by lukehappy on 2008-12-08
Hi, I am trying to connect the the internet directly from my computer(Ubuntu) to the internet through a wireless broadband device.

---

### Post by bumanie on 2008-12-08
If you have the .inf files extracted, go to terminal Applications --> Accessories --> Terminal. In terminal type > sudo ndisgtkThen hit Enter. Then put in your password - note there is no visual output when typing the password, but upon finishing, hit enter and the ndiswrapper GUI should appear, it should then be easy to find the .inf file to add to ndisgtk. After reboot the internet should work. I did this recently on a laptop - it worked fine - so good luck.

---

### Post by lukehappy on 2008-12-08
Hi, thankyou for sticking with me for this :-)

I have learnt about mounting. So I could access all the driver files directly from windows partition, Ok in the driver folders there are about seven .inf and as many .sys, as far as I could see windows points to a .sys as the driver so I tryed afew different .inf and then I tryed all .inf. I restarted each time. All .inf were accepted as valid files but only one of the whole set I put on came up with assosiated hardware. I forgot to make a note of it but it was not one of the likley looking ones that had usbmodem.inf in the name so.....I dont know, nothing helped as far as I could see.

I generated the previously requested output.. and attached it. I hope that puts it in a window border for you. otherwise there may be an attachement here somewhere.

---

### Post by lukehappy on 2008-12-08
here is the output that is in the above attachment):P

lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
09:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

==================================================================================================================================

lsusb
Bus 007 Device 002: ID 064e:a110 Suyin Corp. 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 19d2:2000  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

=====================================================================================================================================

 lshw -class network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:a3:06:1f
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:b2:cc:ac
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 86:30:e0:fe:1a:8b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by joeyjoey on 2009-01-12
I have this exact model of modem with Telstra and am trying to set it up on Kubuntu. I am new to Kubuntu and am not sure what to do. I have read lots of pages on setting up wireless but this is the closest one I have found to my model. Can anyone help me with step by step instructions because I am afraid I have read so much it has confused me and I don’t know where to begin. What I was intending on doing was installing inf file and then configuring kppp. However I am not sure what else needs to be done. Any help will be hugely appreciated.  

Thanks!

---

### Post by trainman186 on 2009-03-20
I'm not entirely new to Linux or ubuntu, however this one has me stumped too.
MF636BP is the USB modem.
I have got it to the point it appears to connect using wvdial, then 2 seconds later drops out with a "Modem hung up" error in pppd.
And that was before I tried to install the drivers through ndiswrapper.
lukehappy: the output of lsusb you attached shows the modem is still in its CD-ROM guise. The last post in this **[thread]("http://ubuntuforums.org/showthread.php?t=1065934")** has details on how to switch it to modem mode.
Contrary to that post, you don't need to reboot, just unplug the modem, restart hal ```
sudo /etc/init.d/hal restart
``` then plug it back in again.

That said, I can't get any further either. Looks like we're hung out to dry for the time being. At least I know I'm not alone with this issue.

---

