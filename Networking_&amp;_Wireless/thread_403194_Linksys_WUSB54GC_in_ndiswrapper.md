---
title: "Linksys WUSB54GC in ndiswrapper"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by niviq on 2007-04-06
Hi!
I am trying to install a Linksys WUSB54GC (13B1:0020) network-adapter trough ndiswrapper.
Installing the driver is pretty easy, and ndiswrapper confirms that the device is present. But the device is not any futher usable - for example doing a [FONT="Courier New"]sudo /etc/init.d/networking restart[/FONT] results in it saying [FONT="Courier New"]No such device[/FONT], and neither can any other tool use it.
When trying to [FONT="Courier New"]sudo modprobe ndiswrapper[/FONT] an error comes up, saing that the module don't exist.  This message also comes up when printing version information in ndiswrapper:
```

$ndiswrapper -v
utils version: 1.9
driver modinfo: could not find module ndiswrapper

```
I'm using Kubuntu 6.10 (Edgy Eft), kernel 2.6.20.5, ndiswrapper 1.41 + 1.9 utils

I've been also trying to use native Ratlink Linux drivers, but that just pissed me off because of the lack of WPA(2) support. Also trying [this guide]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29") several error occurs when compiling.

Please. I'm already finding Kubuntu very appealing (the apt repository is the favorite part), and I wouldn't like to be forced back to Windows because of lack of hardware support.

Note that I have reinstalled the system once after applying all the native drivers in fear of having tampered to much. AND that I am willing to reinstall again, if needed.

Thanks in advance to everybody that answerers.

---

### Post by niviq on 2007-04-06
Hi!
I am trying to install a Linksys WUSB54GC (13B1:0020) network-adapter trough ndiswrapper.
Installing the driver is pretty easy, and ndiswrapper confirms that the device is present. But the device is not any futher usable - for example doing a [FONT="Courier New"]sudo /etc/init.d/networking restart[/FONT] results in it saying [FONT="Courier New"]No such device[/FONT], and neither can any other tool use it.
When trying to [FONT="Courier New"]sudo modprobe ndiswrapper[/FONT] an error comes up, saing that the module don't exist.  This message also comes up when printing version information in ndiswrapper:
```

$ndiswrapper -v
utils version: 1.9
driver modinfo: could not find module ndiswrapper

```
I'm using Kubuntu 6.10 (Edgy Eft), kernel 2.6.20.5, ndiswrapper 1.41 + 1.9 utils

I've been also trying to use native Ratlink Linux drivers, but that just pissed me off because of the lack of WPA(2) support. Also trying [this guide]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29") several error occurs when compiling.

I'm already finding Kubuntu very appealing (the apt repository is the favorite part), and I wouldn't like to be forced back to Windows because of lack of hardware support.
And please be quick! Other people in this house are complaining about the wire :-|

Note that I have reinstalled the system once after applying all the native drivers in fear of having tampered to much. AND that I am willing to reinstall again, if needed.

Thanks in advance to everybody that answerers.

---

### Post by Floppyjoe on 2007-04-06
Do you have ndiswrapper-common installed?
Actually it looks like you installed a newer version of ndiswrapper and then did a kernel update which probably wrecked ndiswrapper so it probably needs reinstallation.

---

### Post by river_plate_2005 on 2007-04-06
hey man i think iam going throught the same problem but with tew 424ub adapter usb...
you shuld try

sudo ndiswrapper -m
so it writes itself to modules and try it again.

---

### Post by niviq on 2007-04-06
Nice!
You are right. I upgraded the kernel.  And like you proposed made a new installation of ndiswrapper.
Now it does kind of work. *iwlist* shows all the information correct, but how do I get this working in knetworkmanager? Or how else?
Anyway knetworkmanager right now only says Wired Devices - Wired Network

---

### Post by Floppyjoe on 2007-04-06
In (K)ubuntu 6.10 you need to have all the network interfaces disabled in System/Administration/Networking for (K)network-manager to work properly.

---

### Post by niviq on 2007-04-07
EDIT: :KS Whoa! It started working after i plugged the adapter out and inn again.
Now: How do i get knetworkmanager to start automatically on startup? -AND remember the password


x>>I don't get it. Do you mean network settings:
x>>[[IMG]http://img143.imageshack.us/img143/308/netsettingcs3.th.png[/IMG]](http://img143.imageshack.us/my.php?image=netsettingcs3.png)
x>>What am I spoused to do? If i disable the ONE device that is there, the knetworkmanager stops showing any device.:confused:

---

