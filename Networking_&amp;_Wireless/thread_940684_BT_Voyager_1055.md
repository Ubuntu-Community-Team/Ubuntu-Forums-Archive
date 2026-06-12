---
title: "BT Voyager 1055"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by coubury on 2008-10-07
I followed this quide

> Step 1

Using the file manager in Ubuntu I mounted my windows xp drive and navigated to the above folder. Select the relevant driver files (for the BT Voyager 1055 they are usb8023.sys, RNDISMP.sys and bcmrndis.inf) and copy them to the Ubuntu desktop.

Step 2

Install the latest version of ndiswrapper. I used the Synaptics package manager, searched the cd for packages and selected ndisgtk which also installed the other two ndiswrapper files however you can use the command line – sudo apt-get install ndisgtk

Step 3

In Terminal type “cd Desktop” which will move you to the desktop directory and type

sudo ndiswrapper –i bcmrndis.inf (you will be asked for your user password and you should get an error message which states it will create the file anyway – just ignore and carry on with next steps).

This will copy the bcmrndis.inf to the ndiswrapper folder.

Step 4

Type:

sudo cp –v usb8023.sys RNDISMP.sys /etc/ndiswrapper/bcmrndis/

This will copy the sys files to the ndiswrapper folder.

Extra step if you are using this guide to install a different wireless adaptor otherwise skip to next step:

Type:

lsusb //Note: Is lowercase L

This will bring up a list of all the attached devices for your usb ports. Locate you wireless device in the list and you will see a set of numbers next to it – for BT it was 1690:0715. Make a note of these two numbers.

Step 5

You must now create the hardware configuration file by typing:

sudo gedit /etc/udev/rules.d/99-custom.rules

This will open the text editor for GNOME (KDE users replace gedit with kate) with a blank page. Copy the attached text and save and exit the text editor.

#START**
BUS=="usb",
SYSFS{idProduct}=="0715",
SYSFS{idVendor}=="1690",
RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"
#END**

Please note the single and double quotes on the RUN line which need to be included or your configuration file will not work. If you are installing a different adapter you will need to substitute the two SYSFS numbers above with the ones for your card (see extra step above). After running lsusb BT Voyager shows as 1690:0715 with the first 4 numbers being the idVendor and the second set being the id Product

Step 6

Check the installation by typing:

sudo ndiswrapper –l //Note: Is lowercase L

You should see a message stating Driver: installed and Device: present. This means you have successfully setup the wireless adaptor (if you don't see Device: present unplug your adapter, plug back in and run the above command).

Type:

sudo depmod –a
sudo modprobe ndiswrapper

On the top toolbar, at the right hand side (near the date and time), there will be a icon of a terminal. Left click here and you should see the wireless networks in your area. Click on the network you wish to associate to. If you have security setup up on your router you should be presented with a window to enter your security key.

I had some difficulty with this as I could not connect to my router when security was enabled (even though the router and wireless dongle both support all the current encryption methods) so I had to disable my security through the router and change the mac address table so that only my adapter's mac address can connect to the router. I know this is not the safest of options as mac address spoofing is quite simple to do but it will do for now until I get chance to conduct further tests on the security.

In order to connect to your network each time you boot type:

sudo gedit /etc/modules

And add ndiswrapper to the list that appears in the editor, save and close.


Everything seemed to go ok 

when i type sudo ndiswrapper –l

It says my driver is installed

But when i plug my by voyager adapter in nothing comes up. Ubuntu doesn't recognise it.

when i goto the toolbar near the clock and try and look for wirless connection it only shows an option for my wired connection.

---

### Post by coubury on 2008-10-07
Bump

---

