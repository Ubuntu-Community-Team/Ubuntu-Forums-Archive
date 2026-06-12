---
title: "xf86-input-hyperpen on ubuntu 10.04"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by paganx on 2010-05-05
I've just migrated to ubuntu 10.04 and
unable to get my aiptek hyperpen 6000 working

It last worked with mandriva 2009 (Xorg.conf edited
and worked)

Section "InputDevice"
    Identifier "pen"
    Driver    "hyperpen"
    Option     "Device" "/dev/ttyS0"
    Option     "Mode"   "absolute"
    Option     "Cursor" "Stylus"
    Option    "SendCoreEvents"
    Option     "XSize" "600"
    Option     "YSize" "450"
    Option     "AlwaysCore"
    Option     "BaudRate" "19200"
    Option     "PMin" "62" 
    Option     "PMax" "511"
EndSection

I know it's old but it does the job and at a bit of a loss
without it. please help.

---

### Post by madjr on 2010-05-05
not sure if this might be of help

[http://www.linuxformat.co.uk/forums/viewtopic.php?p=86982&highlight=&sid=d38b8f208293e30dd160af58a5a48f9e](http://www.linuxformat.co.uk/forums/viewtopic.php?p=86982&highlight=&sid=d38b8f208293e30dd160af58a5a48f9e)

---

### Post by paganx on 2010-05-06
I've got the packages from Hardy and the source but the package does not install, the code fails and manual putting the driver in place and editing xorg.conf and still nothing...   The package was not supplied with lucid so I worry I have lost the use of my tablet.

---

### Post by madjr on 2010-05-06
might work for lucid if you can compile it, am not sure what would be the dependencies thou..

else you may need to try the new mandriva, which might be the easiest route

---

### Post by paganx on 2010-05-06
apart from the tablet Ubuntu is a breath of fresh air compared to mandriva.

the most recent source I can find is  1.3.0-3
(throws different errors to the hardy source
but not asking for includes)
 and I have found a binary 1.3.0-4 (different port).
I'm not a coder. So I may have to wait for/find 1.3.0-4 
code as I'm not sure if the edit I have for
xorg.conf is the same either.

---

### Post by paganx on 2010-05-12
still at a complete loss and no idea if the driver will be updated for 10.04.

---

### Post by paganx on 2010-05-28
> **paganx said:**
> I've just migrated to ubuntu 10.04 and
unable to get my aiptek hyperpen 6000 working

It last worked with mandriva 2009 (Xorg.conf edited
and worked)

.

still no sign of a Hyperpen driver for 10.04


I have a

Bus 004 Device 002: ID 4348:5523 WinChipHead USB->RS 232 adapter with Prolifec PL 2303 chipset

Tried setting the USB driver and ubuntu would not reboot ??
not sure if it was the the config but followed the ubuntu 
aiptek USB help file.


any help welcome

---

### Post by paganx on 2010-05-30
hyper pen driver bug


[https://bugs.launchpad.net/ubuntu/+bug/587653](https://bugs.launchpad.net/ubuntu/+bug/587653)

---

### Post by paganx on 2010-06-02
go here for follow ups. 

[http://ubuntuforums.org/showthread.php?t=1495573](http://ubuntuforums.org/showthread.php?t=1495573)

---

