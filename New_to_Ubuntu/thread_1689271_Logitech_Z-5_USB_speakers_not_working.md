---
title: "Logitech Z-5 USB speakers not working"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by Nico34 on 2011-02-16
Hi everyone,

my Logitech Z-5 USB speakers are recognized as a USB device but aren't available in Sound menu:
Most of the times they aren't, but sometimes after a reboot or when I turn my computer on they work fine.
I'm currently on Ubuntu 10.10, but the same thing occurred with Kubuntu, Xubuntu or in the previous Ubuntu installations
[B]
Here is lsusb:[/B]
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:0a13 Logitech, Inc. Z-5 Speakers
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 1058:0730 Western Digital Technologies, Inc. 
Bus 001 Device 003: ID 045e:0761 Microsoft Corp. 
Bus 001 Device 002: ID 07d1:3c0f D-Link System AirPlus G DWL-G122 Wireless Adapter(rev.E) [Ralink RT2870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```[B]

Sound app (when the speakers work they are correctly displayed)[/B]
[IMG]http://i52.tinypic.com/2q2pr86.png[/IMG]

[IMG]http://i51.tinypic.com/k2fxcp.png[/IMG]

---

### Post by Nico34 on 2011-02-17
Up! :)
 
Does anyone have an idea about this?

---

### Post by marin123 on 2011-02-17
connect speakers on usb, run lsusb to make sure they are recognized and then restart pulseaudio server:
```
pulseaudio -k
pulseaudio -D
```

maybe that will get the sound going. i assume, that when speakers are connected before computer is turned on, they work normal. right?

---

### Post by Nico34 on 2011-02-17
Thanks marin123, I tried your code but got an error:

[IMG]http://i181.photobucket.com/albums/x40/Nico34/Schermata.png[/IMG]
[IMG]http://i181.photobucket[/IMG]
It says that the daemon couldn't be launched

---

### Post by marin123 on 2011-02-17
does the sound work?
when i restart pulseaudio daemon few times i also get that message but i have audio.
try killing pulsaudio while playing something (play mp3) and then restart it and see if sound goes off and on.
maybe you cannot start daemon manually because it starts by itself. just like if you try nautilus -k, it restarts by itself...

---

### Post by Gloominati on 2011-02-24
I have exactly the same problem, sometimes after reboot they are recognized but many times they aren't and i have to keep rebooting. got ubuntu 10.10 and non of the tutorials i have found about it apply to my problem since my speakers are not even recognized.

---

### Post by surajit697 on 2011-06-23
[SIZE=4]my logitech USB speaker works after restarting pulseaudio...
actually not restarting... after killing it, when I write "pulseaudio -D" it shows an error msg...

output is like that...

[/SIZE]```
user@user-PC:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 1130:1620 Tenx Technology, Inc. 
Bus 003 Device 003: ID 04b3:310b IBM Corp. Red Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
user@user-PC:~$ pulseaudio -k
user@user-PC:~$ pulseaudio -D
E: main.c: Daemon startup failed.
```[SIZE=4]


now the sound output shows the USB speaker...
here is the attachment of the screenshot of sound preference...
[/SIZE]

---

### Post by marin123 on 2011-06-23
pulseaudio -D gives you error message because the daemon starts automatically when you kill it...
if pulseaudio is giving you trouble, you can configure the speakers in alsamixer and tell all your apps to use alsa.. whenever i can, i tend to use alsa because its faster and doesnt have cracking sounds...

---

### Post by avelach on 2011-06-29
Some time ago I found this workaround fixed the problem:

[https://bugs.launchpad.net/mythbuntu/+bug/584680](https://bugs.launchpad.net/mythbuntu/+bug/584680)

Good luck!

---

