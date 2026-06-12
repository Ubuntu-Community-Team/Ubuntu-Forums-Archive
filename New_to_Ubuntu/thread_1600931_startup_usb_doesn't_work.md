---
title: "startup usb doesn't work"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by mikhaell on 2010-10-19
just put maverick on a usb for an install on laptop. I see the splash screen and then the 10.10 wallpaper but after that nothing... the laptop is currently running windows vista so i would really like to be able to install ubuntu...

---

### Post by amjjawad on 2010-10-19
> **mikhaell said:**
> just put maverick on a usb for an install on laptop. I see the splash screen and then the 10.10 wallpaper but after that nothing... the laptop is currently running windows vista so i would really like to be able to install ubuntu...

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Check the .iso file that you downloaded and then re-create a liveUSB again.

---

### Post by Joshwaa on 2010-10-19
Make sure the ISO is valid, like the post above, check the MD5Sum, and when you manage to get to the menu do a Disk Check :)

---

### Post by mikhaell on 2010-10-20
thanks. i get to the menu- disk check is fine but still nothing. i just get the login sound (sometimes) a blank gnome panel and a wallpaper. any thoughts?

---

### Post by P4man on 2010-10-20
Try nomodeset. When you boot the machine, right after the bios logo, when you see the purple screen with keyboard logo at the bottom, press any key. You should get a menu. Then in f6 menu, select nomodeset. Then "try ubuntu" or whatever the main option is called. You can also try the safe graphics option (again not entirely sure about the name).

If that doesnt help, when it stops booting and you get the black screen, press control+alt+f1. DO you get a full screen terminal? If so, it may ask to login (im not sure), if it does log in as 'ubuntu' password is also 'ubuntu'. Type

```
dmesg
```

Your screen will fill with messages. Is there something that keeps repeating at the end?

---

### Post by Hippytaff on 2010-10-20
I had hells delight trying to setup a live usb with 10.10...gave up and burned a cd instead :-)

---

### Post by C.S.Cameron on 2010-10-20
Startup Disk Creator from the Live CD worked fine for me with 10.10.

---

### Post by mikhaell on 2010-10-20
you were right it was indeed the nomodeset. I changed it and was able to install- but on restart it still freezes on flash screen!
any ideas?

---

### Post by wojox on 2010-10-20
You need to add nomodeset to the kernel line. What video card are you using?

---

### Post by mikhaell on 2010-10-20
nvidia i think.

---

### Post by P4man on 2010-10-20
> **mikhaell said:**
> you were right it was indeed the nomodeset. I changed it and was able to install- but on restart it still freezes on flash screen!
any ideas?

Yes. Nomodeset :)

You can test by going in to grub: press the shift key immediately after the bios screen dissapears. In grub menu, press E for edit. Select a line that looks like this one:

```
linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=2dd4dbe5-9a9e-43c7-b686-1c46681dfdb9 ro quiet splash 
```

(numbers could be different)  Press END to go to the end of the line and add nomodeset there, so it looks like

```
linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=2dd4dbe5-9a9e-43c7-b686-1c46681dfdb9 ro quiet splash nomodeset
```

Press control X to boot. If that works, then it will only last for single session, Next boot you will have to do it again, so to make it permanent, open a terminal and type

```
 gksudo gedit /etc/default/grub
```

IN the that text file, find
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
and again add nomodeset
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```
Save the file, exit gedit, and in the terminal update grub:

```
sudo update-grub
```

---

### Post by mikhaell on 2010-10-21
thanks! i actually only did the first part of what you said- after control x it has been reloading every time properly (except for the splash screen which is a bit off but that doesn't really matter to me). What is nomodeset btw?

---

### Post by P4man on 2010-10-21
nomodeset prevents the kernel from loading a videodriver until the X server (the "gui") is started. With nomodeset, instead, the BIOS video is used during the boot process like in the "old" days. That also explains why your splash is a bit off. Try pressing the auto adjust button on your monitor, if the boot takes long enough for the monitor to adjust to that mode.

The real question is: why on earth linux wants to load a videodriver and set graphic modes only to display a splash screen for a few seconds ? Its got to do with aesthetics and less screen flickering during the boot process due to modeswitching I guess, but it doesnt always work and the upside isnt that great. It shouldnt be the default IMHO.

Kinda weird the setting stuck though. Unless you installed the nvidia drivers meanwhile, that might solve it too, as the nomodeset is probably only needed for the opensource nouveau drivers provided out of the box. If you installed the proprietary nvidia drivers, you probably dont need nomodeset anymore.

---

### Post by P4man on 2010-10-21
BTW, it just struck me this is something that should be improved in ubuntu. If you install with the nomdeset flag enabled, its probably because you need it and logic dictates you will need it again when you reboot after installing, so it should be set by default if it was set in the live session.

At the very least the installer should ask. If one of the option in the F6 menu like nodmraid or nomodeset was enabled, if you want to preserve those for your install.

Where do I suggest something like that? Brainstorm? No one will notice it there. Could this be considered a bug?

edit: filed a bug report and nominated it for 100 papercuts:
[https://bugs.launchpad.net/hundredpapercuts/+bug/664526](https://bugs.launchpad.net/hundredpapercuts/+bug/664526)

---

