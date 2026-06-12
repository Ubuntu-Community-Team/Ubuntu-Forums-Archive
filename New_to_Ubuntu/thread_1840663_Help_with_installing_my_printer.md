---
title: "Help with installing my printer"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by smiley07 on 2011-09-08
I have for the most part done all of the steps found here: [http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714).

My problem is I don't understand how to add:  ```
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
``` to my  /etc/fstab file.

I also couldn't get ```
/etc/rc2.d/S19cupsys restart
``` to work.


I kept getting back:
```

bash: /etc/rc2.d/S19cupsys: No such file or directory

```Can someone help me, step by step because I have no clue what I'm doing. Everything has been installed for the most part except for the 'usbfs' file.

---

### Post by alphacrucis2 on 2011-09-08
> **smiley07 said:**
> I have for the most part done all of the steps found here: [http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714).

My problem is I don't understand how to add:  ```
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0
``` to my  /etc/fstab file.

```
sudo nano /etc/fstab
```

or if you like a GUI editor:

```
gksudo gedit /etc/fstab
```


Edit: I just had a look at your link. It is very old so I would be suspicious of it. Things change a lot over six years.

---

### Post by smiley07 on 2011-09-08
> **alphacrucis2 said:**
> Edit: I just had a look at your link. It is very old so I would be suspicious of it. Things change a lot over six years.

What should I use then?

Also, using:

```
sudo nano /etc/fstab
``` opened the file. What do I do now? 

^O will write something to /etc/fstab should I use that command? Then, do I just type:

```
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 
```

---

### Post by 3rdalbum on 2011-09-08
**STOP.**

You're following a guide from 2006. This isn't Windows XP where the operating system stays the same for ten years - this is Ubuntu where there's a new version every six months. The guide you've been following is ten versions old and some things have changed.

Exactly what printer do you have? Have you tried doing a Google search for the name of your printer and "ubuntu", for instance: "lexmark x1200 ubuntu"?

Just for completeness, I'd like to know whether you've taken a look at the Printers panel (press Alt-F2 and type "system-config-printer") and just tried adding your printer that way. A lot of ex-Windows-users still have the mindset of "I have to install a driver for my printer" when actually there's already a driver included with Ubuntu, and all you have to do is tell Ubuntu that you have that printer.

---

### Post by Azdour on 2011-09-08
Hi,

The OP does not mention which lexmark printer they have but there is a 'slightly' newer forum thread on installing lexmark printers that may help here:

[http://ubuntuforums.org/showthread.php?t=1507972](http://ubuntuforums.org/showthread.php?t=1507972)

---

### Post by smiley07 on 2011-09-08
> **3rdalbum said:**
> 
Exactly what printer do you have? Have you tried doing a Google search for the name of your printer and "ubuntu", for instance: "lexmark x1200 ubuntu"?


I have a Lexmark X1150. And I found that guide using a Google search, it was like the first thing that showed up, so that's why I tried to use it!

> **3rdalbum said:**
> 
Just for completeness, I'd like to know whether you've taken a look at  the Printers panel (press Alt-F2 and type "system-config-printer") and  just tried adding your printer that way. A lot of ex-Windows-users still  have the mindset of "I have to install a driver for my printer" when  actually there's already a driver included with Ubuntu, and all you have  to do is tell Ubuntu that you have that printer.


I tried that, but it doesn't work (I think). I don't see my Lexmark printer X1150 anywhere. It just asks me to enter the device URI or if I have a network printer to type in the host? I don't have a network printer, and I don't know what the URI is.

---

### Post by smiley07 on 2011-09-08
> **Azdour said:**
> Hi,

The OP does not mention which lexmark printer they have but there is a 'slightly' newer forum thread on installing lexmark printers that may help here:

[http://ubuntuforums.org/showthread.php?t=1507972](http://ubuntuforums.org/showthread.php?t=1507972)

This worked! Thank you!

---

