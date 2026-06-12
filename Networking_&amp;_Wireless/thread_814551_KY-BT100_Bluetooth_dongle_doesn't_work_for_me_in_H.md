---
title: "KY-BT100 Bluetooth dongle doesn't work for me in Hardy"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by magna_maxima on 2008-05-31
Hello! I have searched various forums and Google hits for a solution to this difficulty. If anybody can provide some guidance, I'd appreciate it greatly!

I purchased a KY-BT100 USB Bluetooth dongle, labeled as a "Dtech 55-in-1 card reader," about a year ago from ThinkGeek. I simply want to add Bluetooth functionality to my Hardy 8.04 box. It seems the dongle is detected in principle, but I cannot *do* anything with it.

```
jennifer@aeneas:~$ lsusb
Bus 002 Device 006: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 002 Device 005: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 004: ID 05e3:0606 Genesys Logic, Inc. D-Link DUB-H4 USB 2.0 Hub
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 002: ID 03f0:0b0c Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000
```

According to Synaptic, I have installed the following packages:

```
blueman
bluemon
blueproximity
bluetooth
bluez-audio
bluez-cups
bluez-gnome
bluez-utils
gnome-bluetooth
kdebluetooth
libbluetooth2
libbtctl4
libgnomebt0
libkbluetooth0
nautilus-sendto
obex-data-server
python-bluez
totem-plugins
```

Blueman reports "no adapters found" on my system even after [FONT="Courier New"]sudo /etc/init.d/bluetooth restart[/FONT] gets the OK, or after a system reboot.

What can I do to get Ubuntu to work with this dongle? My principal interest in all this is BlueProximity (as opposed to just sending/receiving files off my mobile).

Thanks so much in advance if you can recommend any further packages or tweaks! :KS

---

### Post by monojohnny on 2008-06-13
Hey magna_maxima,

I think your getting the same thing as I did: possibly there is a problem with the startup script for the bluetooth stuff:  - try this for a quick test:

In the startup script (/etc/init.d/bluetooth) there are two lines like this:

SDPD=/usr/sbin/sdpd
...
"test -x $SDPD || exit 0"
...

I found on my 8.0.4 there is no file called 'sdpd', so (as a quick test) commented out the 'test' line completely then "sudo /etc/init.d/bluetooth start" and it worked for me.... See if it works out for you....

Cheers

John

PS:

See my reply on an earlier posting for some more detail: (and also look at the previous postings on the same thread - which is where I got the idea from in the first place).

[http://ubuntuforums.org/showthread.php?t=392407&highlight=bluetooth](http://ubuntuforums.org/showthread.php?t=392407&highlight=bluetooth)

---

### Post by magna_maxima on 2008-08-05
Wow, I should check the forums more often! Thanks SO MUCH for this reply! I now have working Bluetooth support; still ironing out difficulties with BlueProximity, but Bluetooth itself is going just fine.

I really appreciate your help!

---

