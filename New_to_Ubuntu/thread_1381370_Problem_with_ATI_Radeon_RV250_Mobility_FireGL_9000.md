---
title: "Problem with ATI Radeon RV250 Mobility FireGL 9000"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by ultimatestrategist on 2010-01-14
[COLOR=#000000][FONT=Segoe UI][SIZE=3]So, my problem is that I'm getting really slow frame rates when I run glxgears (4500 MAX) and I don't seem to be able to run 3D games like Sauerbraten or Scorched3D. Help would be appreciated! I'm new to linux, but I've had someone helping me that knows what they're doing and she's at a loss as well.
[B]
This is my graphics card info:[/B]

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 02)

**And this is my **[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Segoe UI][SIZE=3]**xorg.conf file:**

[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Segoe UI][SIZE=3]Section "Device"
    Identifier      "Radeon 9000"
    Driver          "ati"
    BusID           "PCI:1:0:0"
EndSection

Section "Screen" 
        Identifier      "Default Screen" 
        Device          "Radeon 9000" 
        DefaultDepth    24 
        SubSection "Display" 
                Depth           24 
                Modes           "1024x768" 
        EndSubSection 
EndSection

Section "DRI" 
        Mode 0666 
EndSection 
         
Section "Extensions" 
        Option "Composite" "Enable" 
EndSection

Section "ServerLayout" 
        Identifier      "Default Layout" 
        Screen          "Default Screen" 
EndSection
[/SIZE][/FONT][/COLOR]

---

### Post by halitech on 2010-01-14
You might get better results with driver being changed to radeonhd but not sure. The opensource ati drivers aren't the best. You may want to drop back to 8.04 or unless this is a laptop, change the video card.

---

### Post by ultimatestrategist on 2010-01-14
By mentioning opensource ati drivers do you mean that radeonhd is one?

What would dropping back to 8.04 do?

Yes, sorry, I have a Dell Latitude D600 laptop.

---

### Post by halitech on 2010-01-14
yes, radeon and radoenhd are the open source drivers that come with the default install.

ATI dropped support for their "older" cards and it looks like the card you have is one of them. Xorg made changes at the same time which prevents using the ati proprietary drivers. 

By dropping back to 8.04 you should be able to use the ATI drivers which will give better performance but you take a hit on newer apps not being available.

---

### Post by ultimatestrategist on 2010-01-16
bump

---

### Post by Mark Phelps on 2010-01-16
You need to quit bumping.  There are no ATI restricted drivers that will work with your card and current versions of Ubuntu.

Halitech already mentioned the only two options available.

---

### Post by orawax on 2010-02-11
Have you tried this xorg.conf:
[http://ubuntuforums.org/showthread.php?t=1095102&p=8434683](http://ubuntuforums.org/showthread.php?t=1095102&p=8434683)

---

