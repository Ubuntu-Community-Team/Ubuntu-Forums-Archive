---
title: "Screen resolution Ubuntu8.10 via/s3g Unichrome PM800"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by ib4nez on 2009-02-03
I trashed XP and installed Ubuntu8.10

Screen resolution is currently 800 x 600 with an unknown screen type.

XP reported the graphics card as via/s3g unichrome pm800
(before i trashed XP)

WHere do I getthe latest linux driver or how do I go about changing the res to 1024x768?

The Synaptic app manager indicates that I have the openchrome driver installed, which I assumed would be ok for my graphics card:

xserver-xorg-video-openchrome
X.Org X server -- VIA display driver
 
Would appreciate some help, 800x600 sucks

:D

---

### Post by kansasnoob on 2009-02-03
I would begin by giving auto-detection one more try by going to terminal and:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

In the meanwhile I'm going to personally test something and post back.

---

### Post by kansasnoob on 2009-02-03
Well, I'm glad I tried my next suggestion first. It not only didn't work it froze my computer at the gdm screen so I had to restart in recovery mode and then reconfigure xorg to it's original config.

I also use the openchrome driver and in 8.04 and it's derivatives I always had to manually edit /etc/X11/xorg.conf to get my resolution right, but the same trick does NOT work in Intrepid so I dunno???????????

I've been lucky and had xorg give me the proper options for screen resolution in Intrepid.

Sorry I couldn't be more help.

---

### Post by tomtom1982 on 2009-02-03
Open a terminal, type in

```
gksudo gedit /etc/X11/xorg.conf
```

and change the subsection Display:

Subsection "Display" 
        Depth       8 
        Modes       "1280x1024" "1024x768" 
        ViewPort    0 0 
    EndSubsection 
    Subsection "Display" 
        Depth       16 
        Modes       "1280x1024" "1024x768" 
        ViewPort    0 0 
    EndSubsection 
    Subsection "Display" 
        Depth       24 
        Modes       "1280x1024" 
        ViewPort    0 0 
    EndSubsection 

After this, save, exit and reboot.

You should make a backup before changing the file.

---

