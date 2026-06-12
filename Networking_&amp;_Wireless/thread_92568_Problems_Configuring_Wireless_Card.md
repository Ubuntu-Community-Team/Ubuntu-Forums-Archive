---
title: "Problems Configuring Wireless Card"
date: 2005-11-19
forum: Networking &amp; Wireless
---

### Post by atrophic on 2005-11-19
I just bought a used laptop and it came with no documentation.  I installed The Breezy Badger and everything's running great except the wireless card.  It shows up in the network admin, I've configured it for the network I want to get on, but it will not work.  I've tried playing with the settings via iwconfig but I get operation operation not supported errors.

My educated (read: ignorant) guess is that I need drivers installed (though it is already appearing in network admin, so maybe not?).  My problem is I have no idea what brand/model the card is, and don't know any way to find out since I have no documentation with the machine.  It's a Toshiba Tecra 9000, which appears to have been a series rather than one particular model.

Is there any way to find out the make/model of my internal wireless card from within ubuntu?  Is there something else I might be doing wrong?

---

### Post by Lambert on 2005-11-19
sudo lshw -businfo

Find your device in the list, notice the class then

sudo lshw -C <class>


lspci should also show you the device and a little different info

When you find the device you can go here to see what driver it should use. Compare that to what's on the configuration: line when you ran lshw -C

[http://linux-wless.passys.nl/Hawking_Tech.html]("http://linux-wless.passys.nl/Hawking_Tech.html")

More wireless info can be found here.

[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/")

are you using wep or wpa security?

---

### Post by Wondersaurus on 2005-11-19
Nope.  I Hit The Wrong Button!

---

### Post by atrophic on 2005-11-20
[QUOTE=Lambert]sudo lshw -businfo
[/quote]

that shows:
             eth1      network        Wireless interface

[quote=Lambert]sudo lshw -C <class>
[/quote]

the relevant part of 'sudo lshw -C network' shows:
  *-network
       description: Wireless LAN Card
       product: Version 01.01
       vendor: TOSHIBA
       physical id: 0
       slot: Socket 0
       resources: irq:11
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:43:3f:c5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS

[quote=Lambert]lspci should also show you the device and a little different info[/quote]
I don't believe the device is showing up in this list.

0000:00:00.0 Host bridge: Intel Corp. 82830 830 Chipset Host Bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82830 830 Chipset AGP Bridge (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #2) (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #3) (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 41)
0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
0000:02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:02:08.0 Ethernet controller: Intel Corp. 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)
0000:02:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
0000:02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 32)
0000:02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 32)
0000:02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)


The information I found in those didn't lead me to finding any of the drivers on the links you posted, which makes me think I don't yet have enough info.

I called Toshiba's support number to see if they could tell me where the drivers were (based on part number of the wireless card, PA3070U-1MPC).  They said that support.toshiba.com would have them, and it would be compatible with the Cisco wireless lan card driver.  I tried installing both that and the toshiba wireless lan card drivers that were found under the tecra 9000 model's downloads, both of which said hardware was not present when using ndisgtk to do the install.  So again I'm at a loss.

[quote=Lambert]are you using wep or wpa security?[/QUOTE]

WEP, but if wpa is easier to access from the laptop, I'll switch it over.

---

### Post by Lambert on 2005-11-20
You have a difficult wireless device when it comes to linux and information about it. I did find this page.

[http://www.met.ed.ac.uk/~hcp/t9000.html](http://www.met.ed.ac.uk/~hcp/t9000.html)

It's a little dated but at the bottom it says.

> Oddly, the built-in wireless card that came with the machine appears as a PCMCIA card even though you can't take it out. It needs the modules orinoco, orinoco_cs, hermes. At long last I have found a base station to test it with and it works fine.

So you can try. 

modprobe orinoco
modprobe orinoco_cs
modprobe hermes

then run sudo lshw -C network again and look at the configuration line to see if the device is using the driver.

Then run iwconfig to see if it's being identified as a wireless device.

If these work then add them to the /etc/modules file so they load on boot.

If you go with wpa you need to install wpasupplicant. With this card I would doubt it would work as it looks like little support and old. wpa is rather new. 

Post back your results. If this doesn't work here is what I sould suggest next.

Go to google (or favorite search engine) and search tecra 9000 linux. Look through all the results.
Or, if you need wireless I would suggest finding a pcmcia to use. Do your homework and find one that works out of the box. 

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29)

good luck!

---

### Post by atrophic on 2005-11-20
Tried it all but still no luck.  For the time I've spent on labor, I could have purchased a box of wireless cards that just worked.  But I thought one would be enough so I bought a $25 replacement (that'll work with G as well, so more of an upgrade).  The card I bought is reported to work out of the box with Ubuntu, so here's hoping that's right.

Thanks for all the advice Lambert.

---

