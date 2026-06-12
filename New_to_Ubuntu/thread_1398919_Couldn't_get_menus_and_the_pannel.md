---
title: "Couldn't get menus and the pannel"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by zelalem on 2010-02-05
Hi, I'm using Ubuntu Interpid and last week I got a new 23 inch Samsung LCD monitor. I was using the monitor quite properly but when I opened it today the top part of teh screen is not visible adn I couldn't get the menu and the pannel. I tried to restore the previous session but didn't succeed. I can't use my computer. What shall I do? Pls help.

Thank you.

---

### Post by nhasian on 2010-02-05
have you tried adjusting the screen from the controls on the monitor itself?

---

### Post by zelalem on 2010-02-05
Hi nhasian, thank you for your prompt response.Yes I did that. I tried to move the screen downward (vertically). But it didn't help. All I need is to get into the dialo box that one uses to change the screen resolution. You know I only see the lower half of teh screen and all the menus and the panel are at the top. What do you I should do?

---

### Post by zelalem on 2010-02-05
Hi, I used a different monitor to adjust the screen and now I can see everything. But the screen resolution is not correct. It should have been 192X1080, but I couldn't get these resolution in the setting windows. Only 1280X760 works properly. What should I do?

Thanks again for the support.

---

### Post by Grenage on 2010-02-05
Hi there,

What graphics card are you using, and is the TV getting it's input from the graphics card's DVI, or VGA output?

Are you using a custom xorg.conf file?

---

### Post by zelalem on 2010-02-05
Hi Grenage, I am using teh following graphics card:
VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

BTW, I'm not using a TV. I'm using the monitor with a PC and the PC gets the output from the VGA output. I had some problem (pls look at my previous posting) and deleted teh xorg.conf file but it had the default setting even before I had this problem. I contains the following:

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

I hope I have given you teh necessary info. 

Thanks for your help.

---

### Post by Grenage on 2010-02-05
It might be worth trying a custom xorg.conf, I have a rough guide [here]("http://www.grenage.com/xorg.html").

If you get stuck, post back with your monitor's model number and I'll knock something up.

---

### Post by nhasian on 2010-02-06
before you go messing with the xorg.conf first lets see what video card you have and if you've loaded the proper drivers for it. open a terminal from Applications->Accessories->terminal

then enter:

```
sudo apt-get update && sudo apt-get upgrade
```

depending on what updates you received you may need to reboot.  then check System->Administration->Hardware Drivers

see if there are any drivers for your video card that you can enable.  if that doesnt work, give us the output of the following command:

```
lshw -C display
```

---

