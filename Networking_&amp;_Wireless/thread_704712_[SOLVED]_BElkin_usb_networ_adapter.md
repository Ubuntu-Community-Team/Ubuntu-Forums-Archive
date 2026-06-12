---
title: "[SOLVED] BElkin usb networ adapter"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by carterrocks on 2008-02-22
I've just installed ubuntu and I'm having a hard time using my wireless usb toggle.  I've tried a lot of tutorials but I think their not working because it uses Rt73 drivers, Someone please help!

---

### Post by carterrocks on 2008-02-25
Bump

---

### Post by aeiah on 2008-02-25
first you should confirm that it does indeed need the rt73 drivers. do 

lsusb

in a terminal and see how it describes your usb card (the command will list all your usb ports, and what is connected to them). if it is indeed the rt73, you'll need to install the serialmonkey rt73 driver from the serialmonkey site. there are guides on how to install it on this forum. be sure you blacklist and unload the broken modules that ubuntu loads up by default (this is described in the tutorials you'll find).

---

### Post by carterrocks on 2008-02-25
> **aeiah said:**
> first you should confirm that it does indeed need the rt73 drivers. do 

lsusb

in a terminal and see how it describes your usb card (the command will list all your usb ports, and what is connected to them). if it is indeed the rt73, you'll need to install the serialmonkey rt73 driver from the serialmonkey site. there are guides on how to install it on this forum. be sure you blacklist and unload the broken modules that ubuntu loads up by default (this is described in the tutorials you'll find).

I went into the CDs Driver folder and it did list them as RT73, so do I need to do lsusb?

---

### Post by james_vanb on 2008-02-25
I'm using the same network adapter in xubuntu.  This is the method to install drivers using ndiswrapper and the install cd.

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands (If not using Xubuntu, substitute commands as appropriate):

sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb

I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (My default is mousepad) as follows:

sudo mousepad /etc/modprobe.d/blacklist

add rt2500usb and rt73usb to end of list, save and close.

[b]REBOOT[b]

This where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin".
Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping.

Now install the driver you just copied with the following :

sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf

Insert the wireless adapter.

Now issue the following commands:

sudo depmod -a
sudo modprobe ndiswrapper

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows:

sudo mousepad /etc/modules

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

sudo ndiswrapper -m

Reboot

You should now have a connection. Roaming mode works sporadically, so I manually configure.  Left click on the network manager at the upper right corner and enter manual configuration. Open wifi properties. Untick "enable roaming". Next to Network name, you should be able to click on the arrow and a drop down will show available networks, click on yours. Set Password type to WPA personal.   Set Configuration to Automatic configuration (DHCP). I don't use WEP yet, but if you do, you may have to enter your password in Network password.

Hope this works for you.

---

