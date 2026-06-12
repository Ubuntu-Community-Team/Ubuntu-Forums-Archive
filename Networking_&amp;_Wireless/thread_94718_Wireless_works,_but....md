---
title: "Wireless works, but..."
date: 2005-11-24
forum: Networking &amp; Wireless
---

### Post by axslinger on 2005-11-24
I got a LinkSys WPC54G installed and working, but I have to enter the following commands every time I restart the computer:

```
- sudo iwconfig wlan0 channel YOUR_CHANNEL essid YOUR_ESSID mode Managed (YOUR_CHANNEL and YOUR_ESSID should come from the iwlist)
- sudo ifup wlan0
```

How can I get this card to come up automatically on startup?
Thanks.

---

### Post by Grimoire on 2005-11-24
In a terminal do:

```
sudo gedit /etc/network/interfaces
```
 
Go to the end of the file and add:

```

iface wlan0 inet dhcp
wireless_keymode shared
wireless_mode managed
wireless_nick <the nickname of your wireless network>
wireless-essid <the Essid of your network>
wireless-key <the wireless key of your network in hexadecimal form>
auto wlan0
```

It should end up looking something like this:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0


iface wlan0 inet dhcp
wireless_keymode shared
wireless_mode managed
wireless_nick #####
wireless-essid #####
wireless-key ######
auto wlan0

```

Save and when you reboot it should automatically use the wireless card.

Hope that helps!

---

### Post by aznboi on 2005-11-24
or you can download the gtk wifi application!
[http://prdownloads.sourceforge.net/gtkwifi/gtkwifi-1.09.deb?download](http://prdownloads.sourceforge.net/gtkwifi/gtkwifi-1.09.deb?download)

cd /towhere/you/saved
sudo dpkg -i gtkwifi-1.06.deb
right click on ur panel select add to panel... then choose Wireless Connectivity Manager under the internet category

this tool will scan for AP's for u and then connect to the one u choose

---

