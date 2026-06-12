---
title: "change refresh rate to 100hz - a fail-safe way?"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by poisonborz on 2010-01-21
Hola,

I'm trying to set 100mhz for my SyncMaster959NF monitor in Ubuntu 9.10 (in the NVidia driver panel the max setting is 85hz)

Yes, I know there is a ton of tutorials for changing the xorg.conf file, but I have bad memories with fiddling that from old times, and the monitor will be changed soon, so I want a temporary solution.

The best solution would be to somehow add the 100hz option in the Display settings (either in the default or in Nvidia). Is this possible? Is there a really fail-safe way to change the refresh rate?
Thanks

---

### Post by Zorael on 2010-01-21
*(This may just outright fail with the Nvidia proprietary driver, no idea.)*

You may be able to add a new mode (without toiling in xorg.conf :3) by using **xrandr**, but it would only last for the current X session. You would have to make it be autorun upon X start to make it permanent.

As detailed on [the Ubuntu wiki page on X resolution configuration](https://wiki.ubuntu.com/X/Config/Resolution#Adding undetected resolutions);

> [size=3]Adding undetected resolutions[/size]
Due to buggy hardware or drivers, your monitor's correct resolutions may not always be detected. For example, the EDID data block queried from your monitor may be incorrect.

If the mode already exists, but just isn't associated for the particular output, you can add it like this:
```
$ xrandr --addmode S-video 800x600
```
If the mode doesn't yet exist, you'll need to create it first by specifying a modeline:
```
$ xrandr --newmode <Mode``Line>
```
You may create a modeline using the gtf or cvt utility. For example, if you want to add a mode with resolution 800x600, you can enter the following command: (The output is shown following.)
```
$ cvt 800 600
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
```
Then copy the information after the word "Modeline" into the xrandr command:
```
$ xrandr --newmode "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
```

Now, **cvt** accepts refresh rate as a third argument, so you should be able to divine a 100hz modeline by evoking '**cvt *<width> <height>* 100**'. For instance, assuming 1280x1024;
```
$ cvt **1280 1024 100**
# 1280x1024 99.96 Hz (CVT) hsync: 108.66 kHz; pclk: 189.50 MHz
Modeline **_"1280x1024_100.00"_  189.50  1280 1376 1512 1744  1024 1027 1034 1087 -hsync +vsync**
```
And then you tell **xrandr** to add that modeline to its repertoire.
```
$ xrandr --newmode **_"1280x1024_100.00"_  189.50  1280 1376 1512 1744  1024 1027 1034 1087 -hsync +vsync**
```
I'm not sure if it's automatically added to your screen or if you have to manually assign it, but as that wiki page says you could do this with;
```
$ xrandr --addmode *<output>* _**"1280x1024_100.00"**_
```
Merely running '**xrandr**' should list your outputs' names so you know what to specify there. My netbook has **LVDS1** and **VGA1**.

And lastly, apply the resolution.
```
$ xrandr --output *<output*>  --mode 1280x1024 --rate 100
```

If it works, then you can go ahead and add those three commands (newmode, [addmode] and mode) to your environment's **Xsetup** script, which is run before the login manager starts its greeter. kdm's is at **/etc/kde4/kdm/Xsetup**, and that wiki page suggests GNOME's is somewhere in **/etc/gdm/**.

**edit:** [This wiki page on RandR](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) also has some interesting tips and suggestions.

---

