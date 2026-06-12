---
title: "permission denied"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by slaiyer on 2006-07-24
I am trying to install ndiswrapper but i keep getting errors:

when i run
$sudo make install

i keep getting errors:

[error 1] permission denied creating lib/somethings/misc
[error 2] permission denied blah blah blah...

it seems like i need root persion or something because $sudo doesnt seem to give me the permission to create the directories

---

### Post by catlett on 2006-07-24
I do not know if sudo is your problem but if you want a root terminal, enter this ```
sudo -s -H
```Then enter your regular user password and you will be at a root terminal as if you had entered su and an administtrator password.

---

### Post by slaiyer on 2006-07-24
Okay i was able to install ndiswrapper, but not when i install the netprism.inf file for my DWL-122 use adapter, it say that the driver is invalid...on line 135....so i looked up the line and this is what it says:

 HKR,NDI\params\RTSThresh,ParamDesc,0,%RTSTHRESH_STR%

---

### Post by catlett on 2006-07-24
I never had to deal with ndiswrapper so I don't have experience with it. But where did the netprism.inf file come from? Is that part of a download,package or something you had to configure?
I ask because is it something that you could get another copy? Or modify another one? Could this copy of netprism.inf file be corrupted somehow?
Are you following a specific guide?

---

### Post by slaiyer on 2006-07-24
well that would be funny because i have tried 3 different drivers from different source, one including the one that came with the adapter, and i am using it in windows, so it cant be corrupt.

---

### Post by catlett on 2006-07-24
>  and i am using it in windows, so it cant be corrupt.
Are you using a file that works in windows on linux?

---

### Post by slaiyer on 2006-07-27
Well at first i tried all the drives that were said to be linux compatable, the ones i got from ndiswrapper.sourceforge.net but they gave the same invalid error. So i decide to try with the windows driver, but also the same error. What could be the cause?

---

### Post by catlett on 2006-07-27
It appears you are not alone. [http://www.ubuntuforums.org/showthread.php?t=223683](http://www.ubuntuforums.org/showthread.php?t=223683)
The last post suggested suggested this fix but noone replied to say if it worked or not.
```


sudo gedit /etc/modprobe.d/blacklist
```

and this line
> 
blacklist prism2_usb

save and close.

```
sudo ndiswrapper -e netprism
```
```
sudo ndiswrapper -i ~/NETPRISM.inf
```
```
sudo ndiswrapper -m
```


```
sudo gedit /etc/modules
```

add this line

> ndiswrapper

```
sudo apt-get network-manager-gnome
```

This post has a link to the ndiswrapper troubleshoot wiki but it's server must be down, I can't get into the site.
You may want to check out the link yourself [http://www.ubuntuforums.org/showthread.php?t=222894](http://www.ubuntuforums.org/showthread.php?t=222894)

---

### Post by slaiyer on 2006-07-30
> sudo gedit /etc/modprobe.d/blacklist

I get a command not found error

---

### Post by catlett on 2006-07-30
This what I get when I copy/paste that line from my post 
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

```You can browse to it by going to Places<Computer<Filesystem<etc/modprobe.d and then look for the file blacklist. Just launch nautilus as root so you can make changes to it when you find it. Launch it with this command 
```
gksudo nautilus
```If it isn't there then that is another issue, which might be the root cause of your headaches.

---

