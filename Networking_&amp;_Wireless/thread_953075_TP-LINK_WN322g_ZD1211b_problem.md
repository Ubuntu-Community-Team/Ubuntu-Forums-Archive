---
title: "TP-LINK WN322g ZD1211b problem"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by instinct46 on 2008-10-19
I followed the following instructions to install the ZD1211b drivers and received a couple of problems.

1) Run: **sudo apt-get install ndisgtk**
2) Run: **sudo ndisgtk**
3) It opens a wizard to installing a wireless network driver.
5) Insert the CD with drivers for the device.
4) Click 'Install Driver' and locate the file:
*TL-WN322G\Win98_ME_2K_XP_X64\Driver Files\WinXP\ZD1211BU.INF*
5) Goto NM-APPLET at the top right, and choose wireless networks, which will display available.

My problems are that when I run: **sudo ndisgtk**
the ndisgtk screen loads I select the ZD1211bu drivers I have installed and click 'Configure Network'

I receive the following error messages on the terminal window:

**(Network-admin:11309): Gtk-WARNING **: Unknown property: GtkComboBox.items**

**** (network-admin:11309): CRITICAL **: Unable to lookup session information for process '11309'**

And all connection options: Wireless Connection | Wired Connection | Point to point Connection : Are all locked out "Unselectable".

If I run:

**sudo ifconfig wlan0**
wlan0: error fetching interface information: Device not found

**sudo iwconfig wlan0**
wlan0[INDENT]No such device[/INDENT]

Also if I goto 'System'|'Administration'|'Network Tools' the network tools screen appears, but if I click 'Network device' only (lo) and (eth0) appear and eth0 is my wired network which is working.

Cheers in advance.

---

OS: Ubuntu 8.04LTS
Kernel: 2.6.24-19-generic 2.6.24-19.34
Wifi: USB TP-LINK WN322G ZD1211b

---

---

