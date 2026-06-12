---
title: "xubuntu 6.10 wifi WPA woes"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by mikefinlay on 2006-12-04
Hi,

I've just installed Xubuntu  (totally new to Linux) with success straight off the alternative installation disk on an old PII tower I've cobbled together. It is running like a dream despite the size of the system and seems to be making good use of all the hardware currently in the box. Except the wireless network adapters. 

Now, assuming I can't connect via physical ethernet to the router I'm using (A DLink DSL-G604T with WPA-PSK security running) I have 2 wifi devices plugged in - a Belkin F5D7000 PCI card and a DLink DWL-G122 usb wifi adapter, both of which are in working order.

With both in the machine, my os is recognising them inasmuch as I have, in my network settings window, options for "wireless connection eth0" when my pci card alone is in, and "wireless connection rausb0" as well when I add the usb adapter and reboot.

I appreciate that WPA isn't a tweakable option in the networking window and that I have to fiddle with the /etc/network/interfaces file, by going into terminal and typing gksudo(which apparently allows me to change system things) mousepad /etc/network/interfaces and that brings up a text editor with the file loaded, that I can save post-editing which I couldn;t do opening the file through the browser window.

Now, I've added the following:
> 
auto ra0
iface ra0 inet dhcp 
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "myssid"
        pre-up iwconfig ra0 mode Managed
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK="A shared key"
        pre-up ifconfig ra0 up

replacing ra0 with eth0 and againrepeating the script with rausb0. Then I've saved and in the command line "entered sudo ifup rausb0" (and also eth0) and nothing has happened. Then rebooted with the changes in the interfaces file saved and again, no change, no flicker of life from the leds on my adapters, still showing in the network window though and no hint as to where to go from there. 

I'm guessnig I'm not adding the right things to the script, but I've reached the limit of my understanding. 

Still, I got the bugger installed, so I'm happy. Can anyone help me out and keep me smiling?

---

### Post by mikefinlay on 2006-12-04
Also, I'm not sure how to check whether any changes I'm making are having any difference at all...

---

### Post by mikefinlay on 2006-12-04
ALso, I've just taught myself "lspci" and my system is report ing that  my wifi pci card is a broadcom BCM4306, which is confusing me somewhat - as it says 'Belkin F5D7000' on the card itself. It certainly came in a Belkin box. Very odd. And sligtly more confusing than I was already.

Anyone out there?

<cries like a girl>

---

### Post by FrodoB on 2006-12-04
Yes you device contains a Broadcom chipset, see Passys Site Linux Wireless:
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

You need to use ndiswrapper in all likelihood.


See the ndiswrapper list:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)


General ndiswrapper installation instructions:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)


Using ndiswrapper for a similar chipset:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

Obviously the outline is similar, but the details for your device are different.


Maybe someone who knows a lot more about this than I do can help you if you get into trouble.

---

