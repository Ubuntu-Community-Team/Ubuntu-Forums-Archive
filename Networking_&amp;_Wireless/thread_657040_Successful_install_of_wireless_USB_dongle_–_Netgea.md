---
title: "Successful install of wireless USB dongle – Netgear WG111v2 on Ubuntu 7.04 Feisty"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by David_UK on 2008-01-03
After spending ages reading various instructions for this, I finally got the wireless network running with WEP encription.  I thought it would be useful to document what I did so other new users of linux can refer to it.  Note that I had to move the PC to the router so I could use a network cable connection to download some stuff.

I should point out that my method used far fewer steps than many of the guides I read.  I know that many improvements have been made in 7.04, and perhaps the use of the GUI for ndiswrapper also deals with some of the driver configuration.

1.	Connect to router via cable.  Plug in USB dongle and boot up.
2.	Check what chipset you have in the USB device.  I think I used: ‘sudo lsusb’.  the output gives lots of technical info, but near the bottom I saw ‘0846:6a00’ which is my chipset.  
3.	‘System>preferences>Hardware information’.  Scroll down to ‘WG111v2’, click on advanced and then on ‘USB interface’ below.  Look for info.linux.drivers, mine read ‘rtl8187’.  This driver will have to be blocked so the correct ones can be loaded.
4.	In ‘Synaptic Package Manager’, search for ‘ndis’.  (Ndiswrapper is a utility that allows windows drivers to be used.)  Select ‘ndiswrapper-utils-1.9’ and ‘ndisgtk’ for download.  Accept common also.  Apply.
5.	‘sudo gedit /etc/modprobe.d/blacklist’ opens up the list of blocked drivers.  Scroll to the bottom and add ‘blacklist rtl8187’ on a new line.  Save and close.  This stops the native linux driver starting up when you boot.
6.	Insert the CD that came with the dongle.  Navigate to the drivers folder, and then the ‘win98’ folder (the XP drivers did not work for me).  Copy the .inf and .sys files to a new folder on your desktop (or wherever).  
7.	‘System>admin>Windows Wireless Drivers’.  Direct it to the .inf file you have just copied.  This will install the driver. (You do not have to repeat this for the .sys file.)
8.	Configure the router to show the SSID (network name), and remove any security encription.  
9.	Reboot.
10.	Repeat step 2, the driver should now be ‘ndiswrapper’.  At this stage, the indicator light on the dongle was flickering, but never lit continually like it did in Windows.
11.	‘System>admin>Networking’.  The wireless connection should be shown.  Mine was ‘wlan0’.  Click on ‘properties’, untick ‘roaming mode’, enter the network ESSID – this is the network name.  Don’t worry about the WEP selection at this point, and leave the key field blank.  Configuration = auto. Ok the changes.
12.	Reboot.
13.	Check it’s working: ‘sudo iwlist scanning’ gives a list of networks the device can see.
14.	‘System>admin>Networking’.  Untick the wired connection.  Note that the network manager will keep telling you about changes here.  You can select ‘manual’ my clicking on the icon.  Network manager should seamlessly change between wired and wireless as you plug in/unplug the cable.  I haven’t played with this much.  Wireless still works even if network manager is unistalled.
15.	After a moment you should be able to browse using the wireless network.


Assuming you can now connect to the unsecured network, proceed to WEP encription.

1.	Configure the router to WEP.  In my netgear router, I enter a password in the passkey box, then click to accept.  5 hex keys are generated in the fields below.  Select one of them, and make a note of it.
2.	‘System>admin>Networking’ again.  Configure the wireless network again – Select WEP: Hex, and enter the key you noted in the field below.
3.	Give it a moment to connect.
4.	Configure the router to not show the SSID to increase security if you like, and consider setting up an ‘access list’ if your router allows (only specified IP’s can connect).

---

