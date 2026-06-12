---
title: "Deleting drivers from ndiswrapper"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by justind on 2007-07-08
I can't seem to get rid of the drivers I put in ndiswrapper. How can I delete these? I tried to get rid of them in the filesystem browser but it said that I did not have permission to change it or its parent folder.

---

### Post by justind on 2007-07-08
I got it deleted and I put the inf in that was on the cd that came with my usb adapter, then went to check it and I get the message invalid driver.
```
root@error:~# sudo ndiswrapper -i oemsetup.inf
installing oemsetup ...
couldn't open oemsetup.inf: No such file or directory at /usr/sbin/ndiswrapper line 217.
root@error:~# ndiswrapper -l
oemsetup : invalid driver!

```

---

### Post by kevdog on 2007-07-08
To brute force remove all the installed drivers with ndiswrapper (more than 1 can cause a problem) issue the following command

sudo rm -R /etc/ndiswrapper/*

Then try reinstalling the driver

---

### Post by justind on 2007-07-08
Ok, that worked now it allowed me to install the driver correctly.

How does it look so far?

```
root@error:~# sudo rm -R /etc/ndiswrapper/*
root@error:~# cd /home/error/wireless_drivers/
root@error:/home/error/wireless_drivers# sudo ndiswrapper -i AVWLPNIC.inf
installing avwlpnic ...
root@error:/home/error/wireless_drivers# ndiswrapper -l
avwlpnic : driver installed
        device (124A:4017) present (alternate driver: prism2_usb)
root@error:/home/error/wireless_drivers# sudo depmod -a
root@error:/home/error/wireless_drivers# sudo modprobe -i ndiswrapper
root@error:/home/error/wireless_drivers# dmesg | grep ndiswrapper
[  537.534585] ndiswrapper version 1.47 loaded (smp=yes)
[  537.580139] usbcore: registered new interface driver ndiswrapper
root@error:/home/error/wireless_drivers# 

```

---

### Post by justind on 2007-07-08
I am still missing something, it keeps using the wrong driver this is what lshw -C network has to say about it:

```
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_usb driverversion=0.2.5 link=no multicast=yes

```

I added that driver to the blacklist since it is not the AVWLPNIC.inf driver then I rebooted but it still uses it. This is what the entry in the blacklist file looks like: blacklist p80211_prism2_usb. Did I type it in there correctly?

---

### Post by kevdog on 2007-07-08
I like the way you think....

I think it is just prism2_usb, but one way you can make sure is just to see what drivers you have installed on your system all containing prism in their name.

```
sudo modprobe -l | grep prism
```

I think you find 7 entries returned.  Based on what you find, blacklist the appropriate one.

I think it will be
blacklist prism2_usb

---

### Post by justind on 2007-07-08
You are right, that is the one I need to blacklist the only problem is it will not let me edit my blacklist it is read only for some reason. I tried to restart but that didn't help.

---

### Post by justind on 2007-07-08
Well, I was able to blacklist the driver. I rebooted and it hung at configuring network adaptes so I must have something wrong. I unpluged my wireless adapter and it booted fine.

---

### Post by kevdog on 2007-07-08
```
gksu gedit /etc/modprobe.d/blacklist
```

Thats probably the command you want.

Not sure what to recommend.  In order to use the device, ndiswrapper or other method, you need to boot with the device plugged in.

---

### Post by justind on 2007-07-08
I took the prism2_usb driver off the blacklist and it booted with the adpater in. Why when I do lshw -C network I get this:
```
*-network
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       serial: 00:0a:e9:08:49:af
       capabilities: ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_usb driverversion=0.2.5 link=no multicast=yes

```

It seems to think it is an ethernet device.

---

### Post by kevdog on 2007-07-08
I dont know a lot about prism_usb things.  I would make another post asking for help with prism_usb problems.  There is a poster named Chili who is very good at this type of problem.  He has a prism_usb device and I know he has got it working.

Sorry I couldnt help you.

---

### Post by justind on 2007-07-08
I'll do that, thanks for you help.

---

### Post by kevdog on 2007-07-08
If you cant find any help, do a search for prism_usb or prism drivers.  Look for posts by Chili or Chilli (I cant remember the name exactly).  If no one responds, send him a message.

---

