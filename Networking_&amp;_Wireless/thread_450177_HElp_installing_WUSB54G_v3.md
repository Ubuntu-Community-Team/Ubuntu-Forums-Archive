---
title: "HElp installing WUSB54G v3"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by Peter09 on 2007-05-21
Can anyone help me. On Friday I downloaded the latest iso of Ubuntu and installed it on my sons compaq 1200. all works fine although there is no native ethernet connection on this machine. He had forgotten to bring his wireless USB stick with him so I was unable to try to install it.

When he got home he rang me to tell me that the machine locked up (or ran slowly with the USB stick in it WUSB54G v3). Using the forums I found that the squirrel? drivers should work and I downloaded them from the site. (rt73-cvs-2007051907)

I mailed them to him and he transferred them to the Ubuntu machine.

Over the telephone we went through the installation procedure. All went well until the make when he told me that he seen an error which indicated that gcc found something? far too large!

The Make seemed to complete, however the Make Install would run only using sudo.

The device still is not  working, however it no longer locks the machine. He says he no longer sees any wireless usb drivers on the machine!

I do not expect anyone to provide an answer from this sketchy information, but can anyone give me any pointers on what might be going on or guidance on how to proceed.

Thanks
PC

---

### Post by Peter09 on 2007-05-21
More information
[U][B]
the results of lsusb | grep Link[/B][/U]

Bus 001 Device 002: ID 07d1:3c03 D-Link Systems

[B][U]
the results of dmesg | tail -n5 include the following lines[/U][/B]

idVendor = 0x7d1, IdProduct = 0x3c03
usbcore: registered new driver rt73

**the results of iwconfig ** (not quite sure of the order)

lo no wireless extensions
RT73 WLAN
etc
etc

There is no reference to rausb0 which I presume is the device.

---

### Post by renzokuken on 2007-05-21
this may be a good place to look

[http://ubuntuforums.org/showthread.php?t=192588&highlight=WUSB54G+v3](http://ubuntuforums.org/showthread.php?t=192588&highlight=WUSB54G+v3)

---

### Post by gtfourdreams on 2007-05-21
i had a lot of trouble using my WUSB54G v4 with WPA encryption. i ended up ditching it. so if you're trying to do it with WPA/WPA2, from what i've read i don't think you can (easily, anyhow).

---

### Post by Peter09 on 2007-05-21
Arrrggggg.......

during the general mucking around I blacklisted the RT73 driver:(. I don't know what I did but the USB stick is now seeing the network :D but I have two wireless interfaces specified WLAN and WMASTER:(. It appears that WLAN is the one seeing the network :) but it will not connect with  WPSK:(

Any help or clarificatios would be really appreciated.

---

### Post by Peter09 on 2007-05-22
The wireless device can now see the network (recognise the SSID) but will not connect to . It appears to be on WLAN (there is still a WMASTER device).  The network is usually encrypted but the device will not connect even with an unencrypted network.


Can any one give me the commands to set up the device. I believe that this can be done by removing network manager and entering a set of commands long hand.

Thanks in advance
PC

---

