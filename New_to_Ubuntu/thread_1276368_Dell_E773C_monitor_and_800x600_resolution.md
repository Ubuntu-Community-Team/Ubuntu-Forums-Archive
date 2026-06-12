---
title: "Dell E773C monitor and 800x600 resolution"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by Feyd-Rautha on 2009-09-27
I am really new to the Linux world. I have done some looking around about the issue where my resolution maximum on my first install of Ubuntu 9.04 is 800x600. Here is what monitor I have, this is copied from the System Profiler in Mac OS X.

[FONT=Lucida Grande]**DELL E773c:**[/FONT]
  [FONT=Lucida Grande]  Resolution:    1152 x 864 @ 75 Hz[/FONT]
  [FONT=Lucida Grande]  Depth:    32-bit Color[/FONT]
  [FONT=Lucida Grande]  Core Image:    Not Supported[/FONT]
  [FONT=Lucida Grande]  Main Display:    Yes[/FONT]
  [FONT=Lucida Grande]  Mirror:    Off[/FONT]
  [FONT=Lucida Grande]  Online:    Yes[/FONT]
  [FONT=Lucida Grande]  Quartz Extreme:    Not Supported[/FONT]
[FONT=Lucida Grande]
[/FONT]
[FONT=Lucida Grande]
[/FONT]
This has the ATI 128 bit card installed. In Mac OS X the maximum resolution (if memory is correct) is 1024x768 that has worked in Mac OS X. I was reading around through these forums and Gbase and was getting a little confused on the process. Any help would be greatly appreciated. Thanks !:KS

---

### Post by CatKiller on 2009-09-27
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

According to [this page]("http://support.dell.com/support/edocs/monitors/e773c/EN/ug/about.htm#Specifications"), the values you want are

```
        HorizSync       30-70
        VertRefresh     50-160
```

---

### Post by Feyd-Rautha on 2009-09-27
Fantastic! Thanks for the information and the help. I will give it a shot and let you know how it works out. As I play around with Ubuntu a bit here I think I may be becoming a believer

---

### Post by Feyd-Rautha on 2009-09-27
It worked wonderfully Thanks for all your help. Much cred to you

---

### Post by CatKiller on 2009-09-27
> **Feyd-Rautha said:**
> Much cred to you

It's not just me. Everything I know so far comes from this forum and poking around. I'm sure you'll be helping out here in time.

Welcome to the community.

---

### Post by marcusgoad on 2010-04-15
Thank you very much this fix also allowd me to use nvidia drivers hassle free.

Marcus

---

