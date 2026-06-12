---
title: "Network Manager funny after restart"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by Shmook on 2007-04-12
A funny thing started happening after Network Manager and ndiswrapper have been working fine with my Linksys USB Network adapter. 

The problem is, every time I boot up, Network Manager doesn't have an option for wireless. To fix this, I basically went through the same setup Howto I used to set up ndiswrapper in the first place as well as a wifi help file, and had to:

>sudo modprobe ndiswrapper

>sudo /etc/init.d/dbus restart

After which NM recognizes wireless and lets me put in the network info and key to log onto the WPA wireless network I use. Let it be known that I have no idea why this works (I'm quite new to Ubuntu and Linux).

I don't mind doing this every time I log in, but I'm curious why this might have happened, and if there's an easy way to fix it. Thanks!

---

### Post by dbott67 on 2007-04-12
Can you post the output of:
```
dbott@feisty:/etc$ cat modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
[COLOR=Blue]ndiswrapper  *[COLOR=Red]# if you don't see ndiswrapper listed, you need to add it[/COLOR]*[/COLOR]

```To edit the file:
```
sudo gedit /etc/modules
```and add [COLOR=Blue]**ndiswrapper**[/COLOR] to the end of the file
-Dave

---

### Post by Shmook on 2007-04-12
```
eric@eeee:/etc$ cat modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
eric@eeee:/etc$ 
```

So yes, no ndiswrapper -- but it's odd, the only difference between before the "sudo modprobe ndiswrapper" and restarting dbus is iwconfig. and network manager, of course...

lsusb recognizes it, ndiswrapper says driver installed, device present, but no wlan0 entry under iwconfig...

Nevertheless I'll use your advice; thanks a lot!

---

