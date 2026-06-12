---
title: "Wireless was working, now it isn't."
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by acreman on 2007-03-23
I recently got my wireless card working in Ubuntu Edgy Eft.  My card is based off of the RT2500 device drivers.  I got it working by downgrading my security from WPA-PSK TKIP to WEP.

Today I upgraded my distro from Edgy to Feisty Beta 1.  When I restarted the computer my wireless card no longer worked even though the settings for the card had not changed.  I am wondering if anyone else is having this problem and if you have figured out how to solve it.

Thanks,
acreman

---

### Post by Hendrixski on 2007-03-23
I don't know if it's a problem with Feisty, but sometimes I know that when my wireless card is connecting to the wrong networks it gives the appearance of not working... I used to go through command line to switch it, but then I just installed Network Manager from the add-remove programs, and I can chose my networks from a little menu item.  Very sweet.

I don't know if that helps. hope it does

---

### Post by acreman on 2007-03-23
Sorry but it doesn't.  Feisty comes with NetworkManager Applet 0.6.4 installed.  I can see my network but it won't let me connect.  I've tried ever possible combination for the wireless code and it doesn't work.  Thanks for the reply though.

---

### Post by johntelthorst on 2007-03-24
I don't know if my problem is along a similar vein, but I can only connect to my network with feisty if the SSID is broadcasted.  Has anyone else had this problem?  I'd much rather not broadcast the SSID for security reasons.

---

### Post by dompie on 2007-03-24
I have a similar problem
Wireless worked in 6.04 (with ndiswrapper) but not anymore since installing the beta (herd 4 and 5) and alpha releases of Feisty; after using ndiswrapper (and wifi radar) the hardware and the driver are present, but no connection.
This happened before and after SPA was enabled in the belkin router
Wireless PCI inprocomm 2220 in an ACER ASPIRE 1801

I can add to this that the Canon scanner, that worked perfectly in6.04 and 6.10 is recognised in the Alpha release of Feisty but does not start.
In xsane the RGB data are read (the bar advances and in the preview Isee a blackscreen descending) but that's all.

This happened when dual booting AND when only Feisty is installed (no Win XP)

---

### Post by tmcastberg on 2007-03-24
I'm not sure if it's the same issues, but I had perfectly working wireless in dapper, in edgy and feisty it does not work "out of the box". 
The problem is the new /lib/modules/<kernelversion>/kernel/ubuntu/wireless packages. Simply renaming the folder to prevent the drivers from loading completely solved my problem.

---

### Post by nickmcg on 2007-03-24
I have just done a complete install on a machine which was running edgy quite happily using an RT2570 adaptor.
Under edgy, the adaptor was "rausb0", now it's "wlan0"

The only way I can get this to work in feisty is 
```

sudo ifdown
sudo iwconfig wlan0 essid "ESSID" key [wep key] ap [ap address from iwlist scan]
sudo ifup
```

this works reliably every time.

Does anyone have any idea how I can fix this so that it happens at start up? Does it help anyone else?

Thanks

Nick

---

### Post by chili555 on 2007-03-24
> how I can fix this so that it happens at start up?Sure! Simply sudo gedit your /etc/network/interfaces file to amend the wlan0 section to look something like this: ```
auto wlan0
iface wlan0 inet dhcp
wireless-essid chili
wireless-key 93c8530b2df51711bad5596f91
wireless-ap 00:11:wh:at:ev:er
```

---

### Post by nickmcg on 2007-03-24
> **chili555 said:**
> Sure! Simply sudo gedit your /etc/network/interfaces file to amend the wlan0 section to look something like this: ```
auto wlan0
iface wlan0 inet dhcp
wireless-essid chili
wireless-key 93c8530b2df51711bad5596f91
wireless-ap 00:11:wh:at:ev:er
```

That doesn't seem to work - maybe I need to try a pre-up command  ?

---

### Post by dolphin_oracle on 2007-03-24
This may or may not be related to the original poster's issue, but I recently updraded my edgy installation to the latest kernel and my RT61 based card quit  working.  It turned out I needed to reload the RT61.ko module into the new kernel.   I didn't need to do anything to the configuration file, just need to "make" a new RT61.ko and reload.  I'ld have to look up the specific commands, but their something like depmod and modprobe for the loading.  There is a pretty good tutorial by judgekaster that I used to setup my card.  Here's the link, although i don't know if it applies to your card.

[http://www.ubuntuforums.org/showthread.php?t=132980](http://www.ubuntuforums.org/showthread.php?t=132980)

---

### Post by corneel on 2007-03-24
> **acreman said:**
> I recently got my wireless card working in Ubuntu Edgy Eft.  My card is based off of the RT2500 device drivers.  I got it working by downgrading my security from WPA-PSK TKIP to WEP.

Today I upgraded my distro from Edgy to Feisty Beta 1.  When I restarted the computer my wireless card no longer worked even though the settings for the card had not changed.  I am wondering if anyone else is having this problem and if you have figured out how to solve it.

Thanks,
acreman

I have problems to. My wireless card no longer worked under Feisty after an updat last week.

Corneel

---

### Post by hollinch on 2007-03-28
I have the same problem. I upgaded my 6.10 to Feisty (7.04) beta, and after the upgrade the wireless connection was not established automatically, when it did so perfectly fine in 6.10 every time.

Some observations:
- The wireless applet shows the correct ESSID for my wireless access point, and it shows the key is stored.
- iwconfig shows blank information for essid and key
- sudo iwconfig ath0 key <key> essid <essid> and dhclient got it to work again.
- while booting I noticed that my wireless PCMCIA card (Netgear WG511T with Atheros chip) successfully connects, but loses the connection again before booting is complete. This is shown through the two LEDs on the card, they flash in sync if the connection is successful, and out of sync when there's no connection.
- The settings are not permanent, as every time I boot I get into the same situation, and I have to open a terminal to activate the connection.

I don't broadcast my ESSID and I use 128-bit WEP, but this is not relevant to the problem imho.

Hollinch

---

### Post by kolslorr on 2007-03-29
Uninstall Network manager from Synaptics, and configure it via System>Admin>Networks

Works for me. 

At this stage, Network manager is still a crapware, cant blame it since its still beta, hopefully fixed when released.

---

### Post by JengaBlocks on 2007-03-29
Best thing to do is rebuild the driver for the wireless card. Then go through the same set of operations you did to get it working on the previous install. Keep very careful notes! I do this all the time with the RT2561 card I have. This entire week that's all I been doing whenever I change Ubuntu products from my machine (Desktop, Server, Alternate CD, Xubuntu, etc.)

Good luck

---

### Post by JengaBlocks on 2007-03-29
> **nickmcg said:**
> That doesn't seem to work - maybe I need to try a pre-up command  ?

From my experience, using /etc/network/interfaces for RTxxxx cards doesn't work. You have to give iwpriv commands after the card is up. Go to the ralinktech.com website and download the Linux driver and rebuild. Then, go through the readme and iwpriv readme file.

---

### Post by Jouke74 on 2007-03-29
After latest update to Feisty the same problem for me. I used Ndiswrapper on a Asus Wl-138g Marvel chipset card under Feisty 64 bit. It works flawlessly with Kernel 20.6.9.  With kernel 20.6.**13** there is no connection to my accesspoint. The wirless card is detected nicely, everything boots ok, I can get all networks in network-manager, it tries to connect, need to type the password etc, however there comes no connection when it tries to connect. Also not to an unprotected accesspoint in my area.

---

### Post by nickmcg on 2007-03-29
> **kolslorr said:**
> Uninstall Network manager from Synaptics, and configure it via System>Admin>Networks

Works for me. 

At this stage, Network manager is still a crapware, cant blame it since its still beta, hopefully fixed when released.

Thanks - that's fixed it for me:KS

Nick

---

### Post by nickmcg on 2007-03-29
> **JengaBlocks said:**
> From my experience, using /etc/network/interfaces for RTxxxx cards doesn't work. You have to give iwpriv commands after the card is up. Go to the ralinktech.com website and download the Linux driver and rebuild. Then, go through the readme and iwpriv readme file.
I have been using the drivers from serialmonkey - in this case though, it seems to be network manager throwing a spanner in the works.

Cheers

Nick

---

### Post by kyruz on 2007-03-29
Same issue here. I read somewhere here you have to edit
> etc/network/interfaces
delete everything exept
> auto lo
iface lo inet loopback
then network manager should connect.

My desktop dontt start so I tryed as root
```
gedit etc/network/interfaces
```
then I got
> error accessing 'file:///root/etc/network': File not found
What to do?

---

### Post by nickmcg on 2007-03-30
> **kyruz said:**
> Same issue here. I read somewhere here you have to edit

delete everything exept

then network manager should connect.

My desktop dontt start so I tryed as root
```
gedit etc/network/interfaces
```
then I got

What to do?

You missed the first '/'

either
```
sudo gedit /etc/network/interfaces
```
or as root
```
gedit /etc/network/interfaces
```

Nick

---

### Post by kyruz on 2007-03-30
> You missed the first '/'
Yes I did :mad: 
I found out, but thank anyway :lolflag:

---

