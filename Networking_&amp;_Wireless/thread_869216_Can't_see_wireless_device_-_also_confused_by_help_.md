---
title: "Can't see wireless device - also confused by help file"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by rorschak on 2008-07-24
Installed 8.04.1 desktop on an empty laptop (Zepto Titan, if that means anything to anyone). Smooth install, no problems.

I can't find any trace of wireless networking on the system, so I go to the help file and look up troubleshooting. First point is to open Device Manager via System->Preferences->Hardware Information. But there's no Hardware Information, or anything else with hardware in the title, under System->Preferences.

So what am I doing wrong here?

---

### Post by dub_u on 2008-08-10
Hi, I am thinking about bying a Zepto Titan and install Ubuntu on it too, so I am a bit curious. What WLAN device do you have? Is it Intel's or Zepto's own? I saw there were two options at Zepto's website.

---

### Post by chili555 on 2008-08-10
Open an Applications -> Accessories -> Terminal and type:```
sudo lshw -C network
```Let it think a bit and it will tell you about your ethernet and your wireless. Post the wireless part here and we'll help you proceed.

---

### Post by augie48 on 2008-08-10
I have Belkin G USB Network adapter, get a lot about ndiswrapper, but lost, off the shelf it only works with windows, so will have to search ubuntu forums for help

---

### Post by augie48 on 2008-08-10
also need to join networking and wireless forum, I can only get read-only how do I join?

---

### Post by james_vanb on 2008-08-10
augie48 -

Process using ndiswrapper for Belkin G USB is as follows:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

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

