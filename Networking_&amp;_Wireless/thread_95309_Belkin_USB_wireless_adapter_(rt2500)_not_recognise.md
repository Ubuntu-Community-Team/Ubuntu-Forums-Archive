---
title: "Belkin USB wireless adapter (rt2500) not recognised, please help"
date: 2005-11-26
forum: Networking &amp; Wireless
---

### Post by bailout on 2005-11-26
I have posted about this before but got no replies so I thought I would try again.

I have a Belkin USB wireless adapter (7050 IIRC) which is listed correctly under device manager but doesn't show in networking. I know it uses the rt2500 chipset which according to the wiki should be automatically installed and working.

Most of the posts about this chipset are about pci cards, is it not being installed properly because it is usb? 

Does anyone know how I can get ubuntu to recognise it as a network device and load the drivers?

Many thanks

---

### Post by robotgeek on 2005-11-26
[QUOTE=bailout]
I have a Belkin USB wireless adapter (7050 IIRC) which is listed correctly under device manager but doesn't show in networking. I know it uses the rt2500 chipset which according to the wiki should be automatically installed and working.
Many thanks[/QUOTE]

The ralink usb card is not rt2500, but rt2570. I have known atleast 2 people who have gotten the rt2570 chipset working. 

This is the link to the driver. 
[http://www.ralinktech.com/drivers/Linux/RT25USB-SRC-V2.0.4.0.tar.gz](http://www.ralinktech.com/drivers/Linux/RT25USB-SRC-V2.0.4.0.tar.gz)

More details at the wireless page below, look for rt2750. 
[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

If you need help compiling, i'll be around in #ubuntu

---

### Post by bailout on 2005-11-26
Thanks for the reply. The driver used by windows is called rt2500usb.sys so I think it must be the 2500 chip? I wonder whether ubuntu has the usb version that windows is using or just the pci one?

btw I think belkin have changed chips in the usb adapter without changing the model no so the chip depends on when the adapter was bought.

I notice that the list of cards you linked to says to post a bug if a card isn't picked up that has a ubuntu supported chip, perhaps I will do that as well.

thanks again

---

### Post by robotgeek on 2005-11-26
It would be helpful to post the details of your usb wireless adapter. 
(type lsusb in a console, and paste the pci id)

AFAIK, the chipsets are the same in all the Ralink devices. The drivers under linux are called rt2500 for pci, and rt2570 for usb. 

Anyways, belkin has 2 usb devices 
F5D6050 - atmel (you probably don't have this, this is a 802.11 b card)
F5D7050 - Ralink chipset 

This will either work with the drivers which I pointed out to you, or with the drivers available from [http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

Either ways, the drivers are rt2570. Hope that helps.

---

### Post by bailout on 2005-11-26
Thanks for that. I was assuming that as the win drivers are called 2500 that meant I would need the linux 2500 drivers and they should have loaded automaticcally. 

I will try that lsusb command later (in win at the moment) and report back

---

### Post by bailout on 2005-11-27
I ran the lsusb and it confirms my adapter as a 7050. I dl'ed the driver you linked to but have never installed anything like this before. Assuming the process would be the same I read the wiki page on installing the rt2500 driver but I am a bit stuck.

The wiki page says I have to apt-get various packages to make and install the driver, ie kernel headers etc. Obviously I cannot do this as I can't connect to the internet until I get the adapter working.

Is it possible to do this without a working net connection?

thanks

---

### Post by robotgeek on 2005-12-12
It would be tough, but is possible. The build-essential, linux-kernel-headers are on the installation cd. You will need to download the driver elsewhere, i guess.

---

### Post by crimble65 on 2005-12-20
hi,
     have you tried [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)
John

---

### Post by nijinsky on 2005-12-21
To get this working follow this link
[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)

took me days without success using other methods. This method took 10 minutes

cheers
bob

---

