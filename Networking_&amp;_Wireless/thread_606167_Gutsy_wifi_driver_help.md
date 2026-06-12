---
title: "Gutsy wifi driver help"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by mrsudo on 2007-11-07
i have downloaded ndiswrapper for my trendnet tew-424ub.  i have also got the sis163u.inf driver and the .sys file which apparantly works with this device.  

kevin@a1600n:~$ ndiswrapper -l
sis163u : driver installed
        device (0457:0163) present

kevin@a1600n:~$ lsusb
Bus 002 Device 006: ID 0457:0163 Silicon Integrated Systems Corp. 

kevin@a1600n:~$ iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

kevin@a1600n:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.

what im beginning to believe is the driver is loaded and everything but the device is not enabled.  how would i be able to do this?  i am still learning linux commands but have a grasp at basic ones.

---

### Post by spd106 on 2007-11-07
Is the ndiswrapper kernel module being loaded?

If you run this command you should get a result,
```
lsmod | grep ndiswrapper
```

if not then try inserting the module with this command
```
sudo modprobe ndiswrapper
```

and add ndiswrapper to your /etc/modules file to make it load on boot.

---

### Post by mrsudo on 2007-11-07
> kevin@a1600n:~$ lsmod | grep ndiswrapper

ndiswrapper           233632  0 

usbcore               161584  10 ndiswrapper,gspca,sn9c102,xpad,usb_storage,usbhid,libusual,ohci_hcd,ehci_hcd

and no output from the modprobe.
i gave it a try.  tried reinstalling driver and rebooting all with no success.

---

### Post by wieman01 on 2007-11-07
You also need to blacklist the old (Linux) driver. Do you happen to know which one it is for your card? If you don't blacklist it, "ndiswrapper" won't kick in and hence you won't be able to use the card. See my Ralink tutorial for reference.

---

### Post by mrsudo on 2007-11-07
thats probably the one thing i havent been able to do.  im not quite sure how to find out which driver i have to blacklist

kevin@a1600n:~$ lsmod | grep usbcore

usbcore               161584  10 ndiswrapper,gspca,sn9c102,usb_storage,xpad,libusual,usbhid,ehci_hcd,ohci_hcd

---

### Post by mrsudo on 2007-11-17
still havent gotten it to work.  tried numerous different drivers and methods.

---

### Post by kevdog on 2007-11-17
You might have to google around, but can you tell us the chipset in your usb wireless device.  This is very important since it will give us a clue if a default kernel module driver is already trying to claim the device.  If you are unsucessful, you could always post the entire lsmod statement.

---

### Post by mrsudo on 2008-01-27
it turns out the sis163u.inf file is the right one.  
[URL="http://www.sis.com/download/download_step1.php?id=155939"]http://www.sis.com/download/download_step1.php?id=155939
[/URL]

wired my pc and updated.  the installed the newest ndiswrapper and kernel headers.  
then i uninstalled network-manager and installed wicd.  

then edited my /etc/network/interfaces file to look like this:
```
iface lo inet loopback
auto lo

auto wlan0
iface wlan0 inet dhcp
wireless-essid My_Network
wireless-key 1397975370

auto eth0
iface eth0 inet dhcp

```

rebooted and voila.  i am also using a wep encryption.  if you use wpa than you must change accordingly[URL="https://help.ubuntu.com/community/WifiDocs/WPAHowTo"]
https://help.ubuntu.com/community/WifiDocs/WPAHowTo[/URL]

---

### Post by mrsudo on 2008-03-03
who woulda know eh!

---

