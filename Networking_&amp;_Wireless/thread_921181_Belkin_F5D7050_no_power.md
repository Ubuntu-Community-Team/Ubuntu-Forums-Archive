---
title: "Belkin F5D7050 no power?"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by jdheiden on 2008-09-16
I am attempting to get a Belkin USB wireless adapter to work with the newest Ubuntu 64 bit.  My card is listed as one that should "just work" without any outside intervention.  However, it seems like my adapter is not getting recognized at all.  When I plug the USB adapter in, absolutely nothing happens, the light does not even switch on.  If I go to the terminal screen and type 'lsusb' it is not listed.  The adapter works fine in Vista, and it is not the USB port as a flash drive placed in the same USB port works.  What could be the problem?

---

### Post by james_vanb on 2008-09-16
Have used Belkin USB on both Ubuntu Gutsy and Hardy. Although using 32 bit and not 64. I've always had to use ndiswrapper and the Belkin install CD. Process is:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic (2 files ndiswrapper utils 1.9 and common).

Open terminal.

Remove the following drivers using these commands:

```
sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb
```

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:

```
sudo gedit /etc/modprobe.d/blacklist
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
sudo gedit /etc/modules
```

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

```
sudo ndiswrapper -m
```

Reboot

---

