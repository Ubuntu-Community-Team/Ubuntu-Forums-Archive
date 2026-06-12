---
title: "WUSB11+Ubuntu"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by Not Your Raven on 2007-04-12
EDIT: Exact error added

I recently installed Ubuntu to dual boot with XP. I attempted to connect using my WUSB11 Linksys adapter, using several different methods. Bear with me, as I am completely new to Linux. [This method worked flawlessly]("https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29"), up to the point at which I was supposed to type this in to the terminal:
gksudo gedit /etc/network/interfaces

The interfaces document comes up, and i am supposed to add the following entry:
iface wlan0 inet dhcp
wireless-essid My_Essid
wireless-key1 XXXXXXXXXXXXXXXXXXXXXXXXXX
auto wlan0

I believe my essid is "linksys", so I replaced "My_Essid" with it. 
My problem arises here, as I have an unsecured network. i am not sure what to put for wireless-key1. i tried leaving it blank, putting "none", and deleting the "wireless key-1" entry entirely. The problem step in the guide is this:
sudo ifup wlan0
When I type this, I get an error like this:
duplicate interface
ifup: couldn't read interfaces file "/etc/network/interfaces"

 I can no longer continue, and my  Ubuntu internet does not work. I will reboot and post the exact error here, as I am in XP now.

Help is greatly appreciated.

---

### Post by Not Your Raven on 2007-04-13
Bump?

---

### Post by Not Your Raven on 2007-04-13
I'm really sorry to triple post, but I am extremely frustrated. I have searched the forums and the web, and tried countless guides, none of which worked. Ndis wrapper successfully installed the driver, it says that hardware is present and the driver is installed. I  have an unsecured network. I have edited the network interfaces file by adding the following under wlan0:

iface wlan0 inet dhcp
wireless-essid linksys.

It seems that it is recognizing the device and driver, but not associating it with anything.
When I run iwconfig, I don't even get a listing for wlan0. Maybe my wireless card only runs as another name?

When i run lsusb, it shows the device as present.

What am I doing wrong?

---

