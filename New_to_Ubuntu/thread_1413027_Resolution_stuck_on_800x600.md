---
title: "Resolution stuck on 800x600"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by jdc158 on 2010-02-21
OS Ubuntu 9.10. So I have tried seeking help on this forum for my problem before. But I didn't need any help any more because magically my computer decided to recognise other resolutions. I've been able to use 1024x768 for months. I recently used WINE to play some video games. I rebooted today, and my resolution was right back at 800x600. 

This is my video card. 

Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

Specs on my monitor. 
[FONT=Times New Roman][SIZE=2]
[/SIZE][/FONT] [FONT=Times New Roman][SIZE=2]Scan Frequencies:
Horizontal 31.47K to 80KHz
Vertical 60Hz to 75Hz[/SIZE][/FONT][FONT=Times New Roman]
[/FONT] 
If changing my xorg.conf is what needs to be done please explain how to write it and how to delete the changed file from the boot terminal if it fails. I dont want to have to reinstall just because I messed up the xorg.conf file and im too retarded to know how to get rid of it.

Please help I hate this 800X600 display!!!

---

### Post by byStanderone on 2010-02-22
...have your tried changing the resolution thru system>preference>display ?

---

### Post by jdc158 on 2010-02-22
yes i only have 2 options. 800x600 or 640x480. I did have all the resolutions available now they're gone.

---

### Post by byStanderone on 2010-02-22
...i see, try to findout if you have xorg.conf file in /etc/X11/xorg.conf

should you have one, add the resolution that you want (1024x768) as seen below, by sudo gedit /etc/X11/xorg.conf don't forget to click on the save button before you exit.

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by jdc158 on 2010-02-22
I've tried this before but messed up. What can I do to prevent that?

---

### Post by van_Zeller on 2010-02-22
make a copy of your xorg.conf file, just in case. For custom resolutions, you can run xranrd, a very interesting utility.

Here is a good link:

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html#more-3469](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html#more-3469)

Come back for more help if you need.

---

### Post by jdc158 on 2010-02-23
So I looked over the xrandr link it looks promising. If I put in these commands and some how do it wrong. Is it easily reversed? Or am I going to be in trouble?

---

### Post by paydaydaddy on 2010-02-23
This is worth a try. Open a terminal and enter the following code:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

It has been a while since I have done this, But I believe once you restart X you will have additional resolutions. You may have to reboot. If this does not give you the resolution you need, then you will probably need to manually configure the X file.

---

### Post by van_Zeller on 2010-02-23
> **jdc158 said:**
> So I looked over the xrandr link it looks promising. If I put in these commands and some how do it wrong. Is it easily reversed? Or am I going to be in trouble?

No trouble at all, you just restart your computer, and it will be back to default resolution, in your case, 800x600.

To make changes permanent, see the rest of the article. So feel free to experiment, if things go wrong, just restart. When you get everything right make changes permanent. Also, be sure to mark the thread as solved if you suceed and come back with more details if you dont. Good luck!

---

### Post by jdc158 on 2010-02-24
Today when I booted all my resolutions were available. What can I do to insure that it will stay?

---

### Post by Mark Phelps on 2010-02-25
> **jdc158 said:**
> Today when I booted all my resolutions were available. What can I do to insure that it will stay?

Stop using Wine ... (oh oh ... hears the hoards of Wine users arming to the teeth to come get me!!)

But more seriously, if Wine is changing your screen resolution, and you've already customized an xorg.conf, and that STILL does not work, you're likely to have to deal with this every time you use Wine.

---

