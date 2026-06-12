---
title: "Belkin F5D5070 V3 - can see networks but not connect"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by pspsampsp on 2008-10-01
I am a noob to ubuntu so please tell me things in a slow and gentle voice or else ill; get confused :confused: 

I have the belkin f5d5070 v3 usb wireless adapter and in ubuntu i can get it to see the network but not connect. I have tryed googleing this but i cannot find information on my specific adapter. i know it is not a problem with my AP as it works with my psp and used to work when i had windows on my pc.
Please if you can help me thanks Sam

---

### Post by james_vanb on 2008-10-03
Network Manager in upper right corner - left click and see if your network is listed - click and attempt connect.  If security is enabled on router (WEP, WPA, etc) - Disable and see if it connects.  Reboots in between changes sometimes helps.  Configuring security can have its own issues.

If you mean the F5D7050 V3 and you have the belkin install cd, I have used it but had to install drivers with ndiswrapper as follows:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic (2 files ndiswrapper utils 1.9 and common).  You will have to replace commands unique to kubuntu as necessary - the following are commands for ubuntu and xubuntu (should only be the commands related to your text editor - I think kdesu or nano is the text editor for kubuntu).

Open terminal.

Remove the following drivers using these commands:

```
sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb
```

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu - kdesu or nano for kubuntu) as follows:

```
sudo nano /etc/modprobe.d/blacklist
```


add "blacklist rt2500usb" and "blacklist rt73usb" (Without the quotes) to end of list, save and close.

REBOOT

Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin". Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following:

```
sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf
```

Insert the wireless adapter.

Now issue the following commands:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows (If you are using Xubuntu, replace gedit with mousepad):

```
sudo nano /etc/modules
```

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

```
sudo ndiswrapper -m
```

Reboot

---

