---
title: "Tether HTC Wizard with Ubuntu 8.10"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by ndennen on 2008-11-23
Hello My Fellow Ubuntu lovers!

I think i may have done something unrepairable but thought i would share what i have done before reinstalling to see if anyone has any insight.

My goal is to tether my t-mobile MDA (HTC Wizard) to Ubuntu 8.10 to share its GPRS cellular Internet connection.  The MDA device is running WM6 cooked ROM from XDA developers.   I have tried both "Internet connection sharing" and "modem link".   Both work as advertised on Windows XP.   

Here is what I did.  
1) I tried to use synce.  I installed the service but was only partially successful.  I think that is because the documentation was meant for ubuntu 8.04.  I followed the documentation here -   [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)
 never got past the command:
sudo rmmod rndis_host cdc_ether usbnet

It appears that Ubuntu 8.10 already has support for tethering many of the devices.   So this is where i think i broke it.  After reading many other "how tos"  The phone is not being automatically recognized as a modem or as a network adapter.

When I try to use internet connection sharing i can do: 
sudo lsusb -v

This shows the phone as

Bus 001 Device 009: ID 0bb4:0303 High Tech Computer Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         3 RNDIS
  bMaxPacketSize0        64
  idVendor           0x0bb4 High Tech Computer Corp.
  idProduct          0x0303 
  bcdDevice            0.00
  iManufacturer           1 HTC
  iProduct                2 Generic RNDIS
  iSerial                 3 00826335-6679-0163-5800-0050bf3f5173

When i try to use the device as a modem it shows up as:

Bus 001 Device 011: ID 0bb4:00cf High Tech Computer Corp. SPV C500 Smart Phone
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass           32 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0bb4 High Tech Computer Corp.
  idProduct          0x00cf SPV C500 Smart Phone
  bcdDevice            0.90
  iManufacturer           1 HTC
  iProduct                2 Generic Serial
  iSerial                 3 00826335-6679-0163-5800-0050bf3f5173


This shows the the device IS being recognized correctly, but that the network manager is not automatically recognizing it.  How can i fix this?
Thanks in advance for all your help and let me know if you need any additional info.

-Nate

---

### Post by ndennen on 2008-11-24
OK...

Here is an update.  I have another machine running 8.04 and 8.10 in addition to my laptop.  8.04 does not automatically recognize the htc wizard as another network card.  THE OTHER 8.10 MACHINE DOES!!!   

I had internet on that machine in about 20 seconds.   SO my problem is that i must have hosed my 8.10 laptop somehow.  Any ideas how i can renenable the support without wiping and reinstalling ubuntu?

Thanks,

-Nate

---

