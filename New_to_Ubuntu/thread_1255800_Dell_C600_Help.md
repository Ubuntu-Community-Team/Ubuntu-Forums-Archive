---
title: "Dell C600 Help?"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by seedlings on 2009-09-01
I'm trying Ubuntu (9.04) again, this time on an old Dell Latitude C600, service tag 9F59H01.

The Ethernet port has never worked (bought used), and without built-in wifi on this machine, I've used a USB connection to the 2wire modem.

Just blasted windows out and I need help figuring out how to get the internet back on.  USB recognizes drives, but the 2wire modem doesn't show up when connected.

I'll also need some pointers to get the video driver.  I read somehing about that while searching, but need the internet first.

CHAD

---

### Post by st33med on 2009-09-01
```
lspci
```

Do that command in the terminal and post it here.

---

### Post by seedlings on 2009-09-01
> **st33med said:**
> ```
lspci
```

Do that command in the terminal and post it here.

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:03.1 Cardbus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE(rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB 
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ES Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)

I typed all that, so there could be a typo.

CHAD

---

### Post by st33med on 2009-09-01
OH I did not read that it was a USB connection, my bad.  

Try following these instructions:
[http://ubuntu-unleashed.com/?s=2wire](http://ubuntu-unleashed.com/?s=2wire)

EDIT: Go up to sudo iwconfig and stop there. There should be no more setup required.

---

### Post by seedlings on 2009-09-01
I have a 2wire 1701hg modem.  I use the modem's wifi for other computers in the house, but for this Dell C600, I must connect a usb cord directly to the modem.  This is how I used it with windows.

Do I need to add a network connection for the USB under System >Preferences >Network Connections ?

CHAD

---

### Post by MrWES on 2009-09-01
> **seedlings said:**
> I have a 2wire 1701hg modem.  I use the modem's wifi for other computers in the house, but for this Dell C600, I must connect a usb cord directly to the modem.  This is how I used it with windows.

Do I need to add a network connection for the USB under System >Preferences >Network Connections ?

CHAD

With the usb dongle plugged in; goto System | Administration | Hardware Drivers -- check if there are any drivers listed for your wireless dongle.

Bill

---

### Post by seedlings on 2009-09-01
> **MrWES said:**
> With the usb dongle plugged in; goto System | Administration | Hardware Drivers -- check if there are any drivers listed for your wireless dongle.

Bill

There are no drivers in use no this system.

Somehow I'm not communicating this problem very well, but thank you all for patience.

I have a wired connection to the modem.  The wire is USB instead of LAN.  I'm not asking about wireless.  I just want to be able to plug the USB cable from my laptop to the modem and surf.  It's like ubuntu doesn't see the modem.

---

### Post by st33med on 2009-09-01
The problem is that most modem's USB drivers are proprietary and not provided for Ubuntu. I am sorry man, but no amount of Googling helped me find a good way to connect via USB to your 2wire set up.

You might want to look up wireless dongle solutions for your computer.

---

### Post by seedlings on 2009-09-01
Grrr, but thank you.  I'll have more questions soon, I'm afraid.

CHAD

---

### Post by anewguy on 2009-09-02
I *think* what you have been saying is that the USB device is purely a network adaptor.  That being said, it may work on it's own, or it might require a driver.  Please post back the output of "lsusb" while the adaptor is plugged in.

Also, I used to have a 2Wire modem for DSL.  Be sure to check the config in it - does it have MAC filtering enabled?  If so, you'll need to do maintenance on the router itself (via http) to include the new MAC address.

Dave :)

---

### Post by st33med on 2009-09-02
> **anewguy said:**
> I *think* what you have been saying is that the USB device is purely a network adaptor.  That being said, it may work on it's own, or it might require a driver.  Please post back the output of "lsusb" while the adaptor is plugged in.

Also, I used to have a 2Wire modem for DSL.  Be sure to check the config in it - does it have MAC filtering enabled?  If so, you'll need to do maintenance on the router itself (via http) to include the new MAC address.

Dave :)

Thread is dead.  He is trying to connect to the modem via USB because the Ethernet port is completely shot on the old lappy.  However, since there is no drivers available for the modem's USB capability, it will not work.

---

### Post by anewguy on 2009-09-02
Are you saying he is trying to connect a USB cable to the external modem?  Sounded to me like he was trying to connect an ethernet cable from a USB network adaptor to the modem, in which case, given that the modem is external, no driver is needed for the modem.  There is the possiblility of a driver being needed for the USB network adaptor, but it may be working on it's own.

I had a 2Wire DSL modem, and to me at least it was rather in a pain to work with.  However, that modem is still an external modem, and mine at least never had a USB connection - only network connections like a regular router or hub.  That is why I was suspecting he was running a USB network adaptor and running a CAT5 cable from it to a port on the modem, in which case the driver issue would be for the USB network adaptor, not the modem.  I can't remember in the thread if anyone ever asked him to do a lsusb with verbose on for the adaptor to see what chipset it was using.  That is the first step that should have probably been taken.

EDIT:  re-read the thread - it DOES sound like he's trying to connect a USB cable to a USB port on the modem, so you are definetly correct - unless he can find a USB driver to communicate with the modem, he'll need another network adaptor.


Thanks for the input!

Dave :)

---

### Post by LewRockwell on 2009-09-02
scrounged up some info on your DSL modem

[http://www.sdboyd56.com/2_Wire/2wire.html](http://www.sdboyd56.com/2_Wire/2wire.html)

and perhaps something referencing laptop

[http://support.dell.com/support/edocs/systems/latc600/en/index.htm#online_documentation](http://support.dell.com/support/edocs/systems/latc600/en/index.htm#online_documentation)

and might further suggest that you find a suitable LAN PCMCIA card to allow the connectivity you desire

.

---

### Post by seedlings on 2009-09-02
Well... I plugged in my son's netopia 3D Reach wireless card to the side slot on the laptop, and ubuntu wouldn't even load.  Froze with blank screen and unmovable mouse pointer in the center.

I restarted without the netopia and then after ubuntu loaded I plugged in the card.  Froze up again.

Is there a budget-el-cheapo wifi card that ubuntu likes?

CHAD

---

### Post by st33med on 2009-09-02
Intel wifi cards work wonders.

---

### Post by seedlings on 2009-09-02
> **st33med said:**
> Intel wifi cards work wonders.

I just picked up a Intel(R) PRO/Wireless 2200BG mini-pci on ebay.

---

### Post by seedlings on 2009-09-08
Wi-Fi came in the mail today... no coax cable, though!  Drat.  Anyway, if I stay close to the modem it works OK.

Thanks again,
CHAD

---

