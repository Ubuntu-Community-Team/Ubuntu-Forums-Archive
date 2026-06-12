---
title: "Can i use VGA drivers for windows in Ubuntu?"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by Rabhak on 2011-01-29
Can i install the VGA driver for windows in ubuntu? the SIS MIRAGE 3+ driver. .  if i could, HOW?

I just bought a laptop yesterday and i installed ubuntu 9.10 on it and my resolution couldn't go beyond 800x600. please help me. . .


My Display Preferences says, Monitor:unknown

---

### Post by uRock on 2011-01-29
Is there any drivers offered when you go in the menus to System> Administration> Hardware Drivers? If yes, then select the one that has (recommended) by it.

You may also want to try installing 10.04. 9.10 will no longer be supported after April. 10.04 is supported until April 2013.

Regards,
uRock

---

### Post by cariboo on 2011-01-29
You can't use windows drivers for your system, they won't work. Have you tried creating an /etc/X11/xorg.conf file? Press Ctrl-Alt-F1, and after you've logged in type the following commands:

```
sudo /etc/init.d/gdm stop
```

The above command will stop the gnome desktop manager. Next you heed to create an xorg.conf file:

```
sudo Xorg -configure
```

This should create a new xorg.conf file in your home directory. copy the file to the proper place:

```
sudo cp xorg.conf.new /etc/X11/xorg.conf
```

The above command will copy the file you just created to /etc/X11, you will probably be asked to replace the existing file, so say yes. 

No you can restart gdm and you should be taken back to your desktop:

```
sudo /etc/init.d/gdm start
```

Unfortunately SIS graphics chipsets are not well supported by the manufacturer, so this is about all you can do.

---

### Post by Rabhak on 2011-01-29
> **uRock said:**
> Is there any drivers offered when you go in the menus to System> Administration> Hardware Drivers? If yes, then select the one that has (recommended) by it.

You may also want to try installing 10.04. 9.10 will no longer be supported after April. 10.04 is supported until April 2013.

Regards,
uRock



No, there is nothing available to click in the hardware drivers. I'm getting frustrated now. . 
i just want to stick to 9.10

---

### Post by robert shearer on 2011-01-29
best search is to prepend 'site:ubuntuforums.org' to your search terms in your favourite browser,  as in....
```
site:ubuntuforums.org SIS MIRAGE 3+ driver
```

in Firefox/Google returns several hits, these being the first few...
[http://ubuntuforums.org/showthread.php?t=1548547](http://ubuntuforums.org/showthread.php?t=1548547)
[http://ubuntuforums.org/showthread.php?t=1410128](http://ubuntuforums.org/showthread.php?t=1410128)
[http://ubuntuforums.org/showthread.php?t=1366936](http://ubuntuforums.org/showthread.php?t=1366936)

---

### Post by Rabhak on 2011-01-29
> **cariboo907 said:**
> You can't use windows drivers for your system, they won't work. Have you tried creating an /etc/X11/xorg.conf file? Press Ctrl-Alt-F1, and after you've logged in type the following commands:

```
sudo /etc/init.d/gdm stop
```

The above command will stop the gnome desktop manager. Next you heed to create an xorg.conf file:

```
sudo Xorg -configure
```

This should create a new xorg.conf file in your home directory. copy the file to the proper place:

```
sudo cp xorg.conf.new /etc/X11/xorg.conf
```

The above command will copy the file you just created to /etc/X11, you will probably be asked to replace the existing file, so say yes. 

No you can restart gdm and you should be taken back to your desktop:

```
sudo /etc/init.d/gdm start
```

Unfortunately SIS graphics chipsets are not well supported by the manufacturer, so this is about all you can do.





I've tried all of this with a success (i guess)but the result is the same. my resolution is still 800x600

---

### Post by 3rdalbum on 2011-01-29
SiS does not really support its graphics chips on Linux, sorry. Can you return the laptop and get one with Intel, Nvidia or even AMD graphics? SiS is pretty pathetic, sorry.

If you really want this thing to work, I'd start by trying Ubuntu 10.10 and seeing if you get the desired resolution. Linux gets better every six months and you're just depriving yourself of potentially a year of bugfixes by sticking with 9.10; some of those bugfixes might be in regards to your screen resolution.

There is also the possibility that you could create an Xorg.conf file and specify your preferred resolution in it. I'll try and help with this but it's been a while since I've had to do this; I'm an Nvidia/Intel user.

**EDIT: Yes, this is different to what the previous poster said. It just contains similar steps at the beginning.**

First, press Control-Alt-F1 to get to a text terminal. Log in there. Now type:

```
sudo service gdm stop
sudo X -configure
```

This creates an Xorg configuration file, in your home directory.

```
sudo rm /etc/X11/xorg.conf
sudo mv xorg.conf /etc/X11/xorg.conf
```

This removes any existing xorg.conf file and moves the new one into the correct place.

Now you can start the GUI again:

```
sudo service gdm start
```

Log in and everything; now open a terminal and run this to edit the xorg.conf:

```
gksudo gedit /etc/X11/xorg.conf
```

You should see a section in this file that specifies what resolutions are available. Have a look at how these are written, and then add your own at the end in the same form. Save your changes and reboot the computer. If this works, then you're done. If this doesn't work, then I don't know what to do. If this causes your graphics to not work, then press Control-Alt-F1 and type:

```
sudo rm /etc/X11/xorg.conf
sudo reboot
```

---

### Post by srs5694 on 2011-01-29
If you're having problems navigating the xorg.conf file, as 3rdalbum suggests, you could try posting it here *as an attachment.* That way those with more knowledge could look it over and offer specific suggestions. There's also documentation online, such as [this FreeBSD page](http://www.freebsd.org/doc/handbook/x-config.html) (just ignore all the stuff about hald, which seems to occupy about 1/3 of that page) or [this article](http://www.linux.com/archive/feed/118108) (it's short on examples, but it tells you what the various sections do).

---

### Post by realzippy on 2011-01-29
Please try a given xorg.conf for SIS graphics from this [link]("http://www.uluga.ubuntuforums.org/showpost.php?p=10343104&postcount=7")

I gave it people with sis/via graphics running maverick several times in the past,it always worked.

---

