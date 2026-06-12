---
title: "Getting a zonenet zew2502 usb wireless adapter to work"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by cubist on 2007-09-14
I bought a Zonenet ZEW2502 wireless usb adapter. I have Feisty 7.04 installed.  I installed ndiswrapper using the applications, add/remove route. I tried to install the driver using ndiswrapper in the GUI. It doesn't show the driver as being installed in the GUI, but when I try to install it again it says that it is already installed. In the terminal,  "sudo ndiswrapper -l" results in "netmw225 : invalid driver!". Note that the actual inf file is netMw225.inf (with an uppercase M). 

I didn't know how to get rid of the driver which wasn't visible in the GUI yet already installed, so I reinstalled Ubuntu - that got rid of it but trying to reinstall gave the same results.

The ndiswrapper website recommends the driver I am trying to install (XP version). 'lsusb' with the adapter in results in '1286:1fab' which corresponds with the information on the ndiswrapper website. Chipset is "Marvell Semiconductor, Inc., Libertas 802.11b/g Wireless" according to the ndiswrapper website.

Any ideas? I didn't have this trouble with another usb wireless adapter which required ndiswrapper.

---

### Post by cubist on 2007-09-15
Bump

---

### Post by cubist on 2007-09-15
I see that the /etc/ndiswrapper folder contains one folder, netmw225. That folder appears to contain nothing. If I get rid of the netmw225 folder will I be able to try to install again? How can I get rid of the folder?

Thanks to anyone who can help.

---

### Post by cubist on 2007-09-21
Alright, I've got it working. In the meantime I had a hard disk fail, but I don't think that was the problem.

I installed the ndiswrapper front end using a wired internet connection and the Applications.Add/Remove (all open source).

I moved both the netMw225.inf file and the MRVW225.sys file from the CD which came with the adapter to my computer and put them in the same spot. (I think my problem was not copying the .sys file).

I ran the ndiswrapper front end program (System, Administration, Windows wireless drivers) and navigated to the inf file I copied from the CD.

I plugged in the ZEW2502. Somewhere here I rebooted.

I ran the ndiswrapper front end again and chose Configure Network. I selected the wireless connection, clicked on Properties, unchecked the Enable roaming mode box, selected the right wireless router under Network name (ESSID), added the WEP code, and set Automatic configuration (DHCP) under Configuration.

Now it's working fine.

It's always the last thing you try that works!

---

### Post by homeriq5 on 2008-02-03
I followed your directions and was able to get my wireless to work, but for some reason every time I restart the system cannot detect the USB device.  When i remove the driver and reinstall it, it starts to work after a minute or so.  Is there something that I can do so that I dont have to keep doing this?

---

