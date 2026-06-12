---
title: "Cannot connect to my wireless connection"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by dibbz on 2007-04-16
OK so I have just recently got Ubuntu and want to set up my wireless connection. I have a Linksy wireless PCI card, and it seems that Ubuntu has detected it since it shows up in Networking along with my Ethernet ports. I can connect to my router via an Ethernet cable, so it's not the router. 

I have tried setting it up, but can't seem to get it to connect. I tried it with WEP, WPA and with no encryption and nothing has worked. One thing though. In the network settings of my wireless card, how do I set it to WEP or WPA? I set it to hexidecimal when I had WEP on and ASCII when WPA was on, and entered in the key in the network password. Is that the right way to do it?

What do I have to do to get this to work?

---

### Post by reauthor on 2007-04-16
In Feisty whit a latest updates is a litle bug whith network manager...If you using Edgy just install network-manager-gnome,very nice litle utility...(sudo apt-get install network-manager-gnome)..So if you have some problem just write here...

---

### Post by dibbz on 2007-04-16
OK I have tried to use ndiswrapper to install a Windows based driver for my card. One problem, I followed all of the steps listed [here](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Installation) but when i run ndiswrapper -l it says invalid drivers. 

I jumped into the device manager and and checked my card. It's listed as a Broadcom even though it is Linksy. I'm guessing Broadcom is the chipset. Anyways on [this list](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) it has both the model of braodcom which is listed as my card in Ubuntu and the Linksy card I bought with the same ID. So I'm guessing I should download the broadcom drivers and use that. 

Now I'm in another problem. I can only download the driver as a .exe. How can I extract the files from the .exe to use with ndiswrapper?

EDIT:- OK I had a hunch that it may not be my drivers, so I tried iwconfig in terminal and it came up with this. 

> 
iwconfig
eth2      IEEE 802.11b/g  ESSID:""  Nickname:"NETGEAR"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Invalid   
          RTS thr: off   Fragment thr: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Does that mean that my wireless card is working? Or are my drivers causing my problem?

---

### Post by Floppyjoe on 2007-04-16
If you are using ndiswrapper and it lists your drivers as invalid then you have a driver problem.
Either you misspelled the drivername or did not use the proper case when issuing the sudo ndiswrapper -i drivername.inf command, or you did not have the necessary files present in the correct directory when doing the install command. It may be that you have the wrong driver also as you suggested.

---

