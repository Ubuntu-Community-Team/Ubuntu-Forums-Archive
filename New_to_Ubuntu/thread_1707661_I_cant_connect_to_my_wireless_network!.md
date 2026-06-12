---
title: "I cant connect to my wireless network!"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by crob26 on 2011-03-15
hello! i am running Ubuntu 10.10 on my dell inspiron desktop and i cannot connect to my wireless network. when i click on the network icon on the top toolbar, it says "Wireless Networks: Device not ready (Firmware Missing)". I am connected to the Internet right now via ethernet, but i would like to be able to use my wireless network. any help is appreciated.

---

### Post by mikewhatever on 2011-03-15
Check out System->Administration->Additional Drivers.

---

### Post by crob26 on 2011-03-15
i tried that but its not bringing up the driver for my wireless card.

---

### Post by Surachinen on 2011-03-15
exacly what model inspiron is it? i had a similar problem with an hp pavilion dv8000

---

### Post by Hippytaff on 2011-03-15
can you open a terminal CTRL+ALT+T and post the output of ```
lspci
```

---

### Post by crob26 on 2011-03-15
> **Hippytaff said:**
> can you open a terminal CTRL+ALT+T and post the output of ```
lspci
```

this is what i got from "lspci"

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by crob26 on 2011-03-15
> **Surachinen said:**
> exacly what model inspiron is it? i had a similar problem with an hp pavilion dv8000

it is a Dell Inspiron 531 Desktop. about 3 years old

---

### Post by Hippytaff on 2011-03-15
BCM4318 - This is probably the culprit

Try [this]("http://ubuntuforums.org/showthread.php?t=190177")

You might need to use the windows drivers with ndisgtk, but we'll cross that bridge if we come to it

---

### Post by Hippytaff on 2011-03-15
Wait...That tutorials too old...don't do the ndiswrapper bit.  I'm a bit busy right now, but if no one replies by the time I get back I'll try to go through using the windows drivers with ndisgtk

---

### Post by cbowman57 on 2011-03-15
Have you tried going into synaptic and adding the firmware-b43-installer already?

---

### Post by crob26 on 2011-03-15
> **cbowman57 said:**
> Have you tried going into synaptic and adding the firmware-b43-installer already?

could you explain a little more.. what is synaptic?

---

### Post by cbowman57 on 2011-03-15
Synaptic Package Manager [http://en.wikipedia.org/wiki/Synaptic_(software)]("http://en.wikipedia.org/wiki/Synaptic_(software)")

---

### Post by mikewhatever on 2011-03-16
crob26, try installing the **firmware-b43-installer** package. The BCM4318 card is listed among those supported.

---

### Post by crob26 on 2011-03-16
> **mikewhatever said:**
> crob26, try installing the **firmware-b43-installer** package. The BCM4318 card is listed among those supported.

alright ill try it, thanks!

---

### Post by josephmills on 2011-03-16
try going to your termainal and typing in 
```

sudo apt-get install b43-fwcutter


```
then restart if that won't work find it in synaptic package manager hope this helps (I hade the same thing happen to me )

---

### Post by crob26 on 2011-03-16
> **josephmills said:**
> try going to your termainal and typing in 
```

sudo apt-get install b43-fwcutter


```then restart if that won't work find it in synaptic package manager hope this helps (I hade the same thing happen to me )

i installed it, but still nothing... could it be because i am just running ubuntu off of my USB? it is not installed onto my hard drive. does it erase everything after i restart? if so, is there anyway i can do this without installing ubuntu on my HD?

---

### Post by Hippytaff on 2011-03-16
hahha...yes...I should have checked how you had installed ages ago - assuming again :roll:

look into [usb persistence]("http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/")

---

### Post by crob26 on 2011-03-17
> **Hippytaff said:**
> hahha...yes...I should have checked how you had installed ages ago - assuming again :roll:

look into [usb persistence]("http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/")
ok i installed b43 with my ethernet connected but nothing happens.. should it automatically install the firmware?

---

### Post by Hippytaff on 2011-03-17
try doing```
sudo apt-get update
```

---

### Post by Hippytaff on 2011-03-17
also - have you rebooted since you installed it (and do you now have persistent usb?)

---

### Post by crob26 on 2011-03-17
> **Hippytaff said:**
> try doing```
sudo apt-get update
```

thanks! you helped a lot, i think i have it up and running now.

and thanks to everyone else who helped, it is appreciated.

---

### Post by Hippytaff on 2011-03-18
You're welcome - Glad you sorted it - Remember to mark the tread as solved in the tread tools at the top of the page...Happy Linuxing

---

