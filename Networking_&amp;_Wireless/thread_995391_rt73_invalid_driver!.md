---
title: "rt73 invalid driver!"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by kwhyles on 2008-11-27
I've tried a few ways to get a Belkin F5D7050 v3000 working on my laptop and I'm running into a problem with ndiswrapper.

I follow these steps:

1. Install network-manager-gnome, ndiswrapper-utils and ndisgtk(probably not necessary) from repository using Synaptic or sudo apt-get. I had to use packages.ubuntu.com since the computer had no wired connection

2. Once ndiswrapper-utils is installed, plug in Belkin USB, and pop in the CD that came with it.

3. Navigate to the WinXP drivers on the CD and copy the rt73.inf and rt73.sys files to your desktop

4. in the terminal (Applications -> Accessories -> Terminal)

```
cd Desktop
sudo ndiswrapper -i rt73.inf
ndiswrapper -l
```

I found these instructions here: ```
http://ubuntuforums.org/showthread.php?t=248059
```

But I get the error 

> Installed drivers:
rt73 invalid driver!

When I try to uninstall the driver using ndiswrapper - e 'driver' both with the file copied to the desktop and the one found in /etc/ndiswrapper/rt73 it says:

> Driver rt73.inf is not installed.Use -l to list installed drivers

Any help please folks...

---

### Post by Ayuthia on 2008-11-28
> **kwhyles said:**
> I've tried a few ways to get a Belkin F5D7050 v3000 working on my laptop and I'm running into a problem with ndiswrapper.

I follow these steps:

1. Install network-manager-gnome, ndiswrapper-utils and ndisgtk(probably not necessary) from repository using Synaptic or sudo apt-get. I had to use packages.ubuntu.com since the computer had no wired connection

2. Once ndiswrapper-utils is installed, plug in Belkin USB, and pop in the CD that came with it.

3. Navigate to the WinXP drivers on the CD and copy the rt73.inf and rt73.sys files to your desktop

4. in the terminal (Applications -> Accessories -> Terminal)

```
cd Desktop
sudo ndiswrapper -i rt73.inf
ndiswrapper -l
```

I found these instructions here: ```
http://ubuntuforums.org/showthread.php?t=248059
```

But I get the error 



When I try to uninstall the driver using ndiswrapper - e 'driver' both with the file copied to the desktop and the one found in /etc/ndiswrapper/rt73 it says:



Any help please folks...

It looks like you tried:
```
sudo ndiswrapper -e rt73.inf
```
If that is the case, you should try:
```
sudo ndiswrapper -e rt73
```

If that is not the case, please post the results of:
```
ls /etc/ndiswrapper
```
This will list the drivers that are currently installed.

By the way, did you ever try the rt73usb driver?  If not, you might try:
```
sudo modprobe rt73usb
sudo /etc/init.d/networking restart
```

---

### Post by gnusci on 2008-11-28
I have one rt73 and it is working fine but I use the serialmonkey driver:

[http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

You just need to download and compile it and install, you need the kernel header files installed, you can install them from the **Ubuntu CD**, adding the CD to the sources list. You can also use the graphical tool **RutilT** to configure the interface.

You also will need to blacklist the following modules:

```

#RT73 SerialMonkey Fix:
blacklist rt2570
blacklist rt73usb
blacklist rt2500usb
blacklist rt2x00lib
#END
```

just add them at the end of the **/etc/modprobe.d/blacklist** file.

---

