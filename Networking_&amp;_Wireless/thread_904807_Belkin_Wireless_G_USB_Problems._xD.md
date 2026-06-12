---
title: "Belkin Wireless G USB Problems. xD"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by mike4life on 2008-08-29
Hi


I'm a total newbie to Ubuntu, and was under the assumtion that wireless worked straight away. :S
I've got a Belkin G USB Wireless Adapter and my computer can't find it. :(
Has anyone else had this problem?



Mike. [x]

---

### Post by james_vanb on 2008-08-29
Have used Belkin USB on both Ubuntu Gutsy and Hardy. Some report that it works out of the box with Hardy. I've always had to use ndiswrapper. Process is:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic (2 files ndiswrapper utils and common).

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

Now install the driver you just copied with the following (If the .inf file you copied is not the rt73, replace as appropriate below) :

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

### Post by Crafty Kisses on 2008-08-29
Post the results of ```
lshw -C network
```

---

### Post by time8man on 2009-04-19
am newbie and thank u very much indeed for the guidance of belkin wireless g network usb adaptor.much appreciated.

---

### Post by james_vanb on 2009-04-20
Glad it helped.  Welcome to ubuntu.

---

### Post by grandsurfy on 2009-10-01
Thank you that sorted my problem:)

---

### Post by james_vanb on 2009-10-01
Good news!

---

