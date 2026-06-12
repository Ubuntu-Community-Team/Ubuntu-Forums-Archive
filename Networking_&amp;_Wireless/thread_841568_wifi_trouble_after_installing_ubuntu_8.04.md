---
title: "wifi trouble after installing ubuntu 8.04"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by mikeric on 2008-06-26
im having a similar problem to one i had on my laptop after upgrading. my wireless is not working. if i run lpsci i get this.
> mike@desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:02.0 Network controller: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter (rev 01)
01:03.0 Communication controller: Agere Systems Unknown device 0620
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


If i run lsusb 
> mike@desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 058f:6377 Alcor Micro Corp. 
Bus 001 Device 003: ID 04a9:1713 Canon, Inc. 
Bus 001 Device 001: ID 0000:0000  
 
Just wondering what i have to do from their, im not sure what wireless card it has.

---

### Post by pytheas22 on 2008-06-26
Did the wireless used to work before the upgrade?  Did you have to do anything special to get it working?

This [thread]("http://ph.ubuntuforums.com/showthread.php?t=718244") might help you; it's for the same kind of Atheros card that you have.

I also read [here]("http://forum.ubuntu-fr.org/viewtopic.php?id=219379") (May 2008), however, that you need ndiswrapper for your card.  I would be surprised if that's really true for an Atheros chip, though; Atheros should work well in Linux.

Try following the instructions in the first thread and see if that gets you anywhere; if not maybe you will have to go to ndiswrapper.

Also, what do you mean by wireless "not working?"  Does it fail to connect?  Does it connect but you can't open web pages?  Can you see wireless networks?  Do you see an entry for your card in Network Manager?  What is the output of iwconfig?

---

### Post by chili555 on 2008-06-26
> Atheros Communications Inc. AR5416 802.11abgn Wireless PCI AdapterThese drivers are supplied by *linux-restricted-modules.*Please open System -> Administration -> Synaptic and, using the search button, make sure they are installed. If they are, go to System -> Administration -> Hardware Drivers and see if you can enable the driver for your Atheros.

---

### Post by mikeric on 2008-06-26
i installed linux-restricted-modules and when i go to hardware drivers it doesnt have any listed.

---

### Post by mikeric on 2008-06-26
I cant get it to connect or view any wireless networks is what i meant.It also doesnt have it listed in the network manager. iwconfig gets this > mike@desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


---

### Post by pytheas22 on 2008-06-26
> I cant get it to connect or view any wireless networks is what i meant.It also doesnt have it listed in the network manager.

In that case, you will probably have to follow the instructions in that thread that I linked to in my first post.  It will have you compile madwifi from source, which might make the difference.

---

### Post by mikeric on 2008-06-26
i got everything working from that above post. Am i going to have to do that for every user? it isnt working on all of the other users set up.

---

### Post by pytheas22 on 2008-06-27
> Am i going to have to do that for every user? it isnt working on all of the other users set up

The wireless card configuration should be global; you shouldn't have to configure anything separately for each user.  What's going wrong exactly that's causing other users to be unable to connect?

Also are you sure that the other users have permissions to use the wireless card?  Go to System>Administration>Users and Groups and click on Properties to see which privileges each user has.

---

