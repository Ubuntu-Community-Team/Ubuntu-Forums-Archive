---
title: "Driver Missing???"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by oscar1776 on 2008-05-28
(Very new to ubunto)

I am trying install a wireless network, following the instructions given on this form.  After trying the first command I'm not sure if I even have the correct driver, if any, for my hardware. I expected to see the last line containing some reference to driver=xxxxx
Could someone please advise me on this issue?

The hardware is a USB card Belkin Model F5D7050.  I have the windows driver but it will not work with ubunto.

 lshw -C network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: 82562V-2 10/100 Network Connection 
       vendor: Intel Corporation 
       physical id: 19 
       bus info: pci@0000:00:19.0 
       logical name: eth0 
       version: 02 
       serial: 00:1d:09:92:58:0a 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=e1000-ich9 driverversion=7.6.5-NAPI firmware=1.1-2 latency=0 module=e1000_ich9 multicast=yes 
  *-network 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:11:50:be:d8:92 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by issih on 2008-05-28
Ok, a bit of investigation leads me to believe your wireless dongle is based on the ralink 2500 based chipset.

These are, in theory, supported out of the box, but I presume that it isn't working as if it did, you wouldn't be posting here :)

my rt73 card also doesn't work with the default drivers, sadly getting it sorted is not that simple...

You have 3 options really:
1) Use the serial monkey drivers:
       [http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)
   You have to compile these yourself, so you'll need various packages
   to achieve this, they also (in my experience) don't integrate with the
   network manager applet properly.

2) Use the ralink drivers
       [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
   Again you have to compile these. These do integrate with network 
   manager.

With both of the above drivers I had terrible trouble getting DHCP to function properly, you may have more luck as your chipset is different, but in the end I gave up on both of them

3) Use ndiswrapper, this program allows you to use windows drivers, its not ideal but it does get most cards up and running. first install the package "ndisgtk" from synaptic package manager. Now you need to extract the information you need from the windows driver, If the driver you have is a nice one, you can treat the .exe file as a zip file and extract things directly, but if its an installshield style application this will not work. In the end I ran the setup.exe under wine and found the files in the virtual c drive.

You need to find the *.inf file that the driver installs, and then give that to ndiswrapper (Open System->Administration->Windows Wireless Drivers)

Hope that makes sense.

It is probable that you may have to blacklist some kernel modules as well, but let us know how much of the above you understand, before we get onto that....sorry its such an utter pig to get working, sadly its one area where ubuntu is not so easy (thanks to a lack of support from the hardware manufacturers)

---

### Post by james_vanb on 2008-05-29
I have Belkin F5D7050 installed on an old Dell Latitiude CP M233St with xubuntu hardy herron and a Desktop running ubuntu hardy herron. Responding on Desktop using Belkin F5D7050, v. 3000 with rt73 driver. Install has been the same using ndiswrapper and the install cd as follows:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands:

sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb


I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:

sudo gedit /etc/modprobe.d/blacklist

add "blacklist rt2500usb" and "blacklist rt73usb" (Without the quotes) to end of list, save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin".  Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following (If the .inf file you copied is not the rt73, replace as appropriate below) :

sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf

Insert the wireless adapter.

Now issue the following commands:

sudo depmod -a
sudo modprobe ndiswrapper

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows (If you are using Xubuntu, replace gedit with mousepad):

sudo gedit /etc/modules

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

sudo ndiswrapper -m

Reboot

---

