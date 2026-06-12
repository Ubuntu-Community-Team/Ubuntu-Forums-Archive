---
title: "More information about my graphics driver problem. 9.10"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by LyonTamer on 2009-11-24
Hello all. Sorry for not posting this as a reply to my previous thread, I am unable to navigate things well with the screen the way it is. 

Anyway, I ran lspci in terminal and it shows I have ATI graphics, not Intel. The exact readout was 01:00.0 VGA Compatible Controller: ATI Technologies, Inc. Rage Mobility M4 AGP

Now, on another thread someone with a similar problem built up a package in terminal. When I ran the code, it came back saying it could not open the ATI installer. The exact readout was:

michelle@michelle-laptop:~$ sh ati-driver-installer-9-10-x86.x86_64.run  - - buildpkg Ubuntu/karmic
sh: Can't open ati-driver-installer-9-10-x86.x86_64.run
michelle@michelle-laptop:~$ 

Again I am running a clean install of 9.10 on a Dell Inspiron 8000

The graphics card works fine with 7.10. Is there a way to install the drivers from that CD?

Please help!

---

### Post by lotharmat on 2009-11-24
Try putting "sudo" (without the quotes) infront of the command.

---

### Post by 3rdalbum on 2009-11-24
DON'T INSTALL THAT DRIVER.

It does not work with your card (much too old). It will cause the total loss of your graphical display.

Unfortunately, ATI does not make a driver for your card that will work on Ubuntu 9.10.

Can you edit your Xorg.conf (/etc/X11/xorg.conf) file and add the desired screen resolution? If the file is almost empty or doesn't exist, then do the following:

Log out
Press Control-Alt-F2, this should take you to a text terminal
Log into this terminal
Type:

```
sudo service stop gdm
sudo Xorg -configure
sudo service start gdm
```

I've never actually done this; but this might actually ask you to specify what resolutions you want, in which case you can do it this way. Otherwise, it should generate a basic Xorg.conf file for you, and then you can edit it to add in the resolution you want.

---

