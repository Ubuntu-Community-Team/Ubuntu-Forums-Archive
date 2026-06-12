---
title: "[SOLVED] Can't find a working video driver"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Vunutus on 2008-12-12
I'm getting frustrated here, every single way I update my video driver ultimately fails in the same way: once I reboot, it goes to the Ubuntu progress bar then the video card shuts down completely, leaving nothing but a "No Signal Input" error on my monitor. I've tried a number of things, including manual installation, EnvyNG, the Hardware Drivers utility, and all the solutions in [this]("http://ubuntuforums.org/showthread.php?t=965180") thread.

How can I get my driver working so I can do anything 3D without dipping to 1 or 2 FPS?

Information: Video card is nVidia 6800, running Ubuntu 8.04 32bit with  2.6.24-22-generic kernel.

---

### Post by overdrank on 2008-12-12
> **Vunutus said:**
> I'm getting frustrated here, every single way I update my video driver ultimately fails in the same way: once I reboot, it goes to the Ubuntu progress bar then the video card shuts down completely, leaving nothing but a "No Signal Input" error on my monitor. I've tried a number of things, including manual installation, EnvyNG, the Hardware Drivers utility, and all the solutions in [this]("http://ubuntuforums.org/showthread.php?t=965180") thread.

How can I get my driver working so I can do anything 3D without dipping to 1 or 2 FPS?

Information: Video card is nVidia 6800, running Ubuntu 8.04 32bit with  2.6.24-22-generic kernel.

Hi and instead of me reading that long thread you link, I will just ask if you have tried using the xfix option in recovery mode after installing the drivers?

---

### Post by PierreDeKat on 2008-12-12
> **Vunutus said:**
> it goes to the Ubuntu progress bar then the video card shuts down completely, leaving nothing but a "No Signal Input" error on my monitor.

I had this "No Signal Input" thing happen to me awhile back, and it was caused by me attempting to set my video resolution to a setting that my monitor wasn't capable of dealing with.

Basically I was just goofing around, and thought I would see what would happen if I set my 4:3 CRT to some widescreen resolution. Things went black, I was forced to reboot, and then it took some finagling to get myself back to normal.

I ended up swapping video cards, just *temporarily*, which forced Ubuntu to reassess my graphics situation, allowing me into my desktop in some low graphics mode, in the process.

Once in, I reset my monitor resolution to something more normal, shut down, went back to my good video card, booted up, reinstalled the proprietary drivers, rebooted, and I was good to go.

Moreover, the problem wasn't the drivers, so much as it was that I was trying to send a signal to my monitor that it couldn't digest. I'm wondering if that might be why your monitor's giving you the "No Signal Input" message.

---

### Post by Vunutus on 2008-12-12
> **overdrank said:**
> Hi and instead of me reading that long thread you link, I will just ask if you have tried using the xfix option in recovery mode after installing the drivers?

Yes, xfix is how I recover my system after the driver breaks it. xfix, however, disables the driver.

> **PierreDeKat said:**
> I had this "No Signal Input" thing happen to me awhile back, and it was caused by me attempting to set my video resolution to a setting that my monitor wasn't capable of dealing with.

Basically I was just goofing around, and thought I would see what would happen if I set my 4:3 CRT to some widescreen resolution. Things went black, I was forced to reboot, and then it took some finagling to get myself back to normal.

I ended up swapping video cards, just *temporarily*, which forced Ubuntu to reassess my graphics situation, allowing me into my desktop in some low graphics mode, in the process.

Once in, I reset my monitor resolution to something more normal, shut down, went back to my good video card, booted up, reinstalled the proprietary drivers, rebooted, and I was good to go.

Moreover, the problem wasn't the drivers, so much as it was that I was trying to send a signal to my monitor that it couldn't digest. I'm wondering if that might be why your monitor's giving you the "No Signal Input" message.

I don't think that's the problem. Even without the driver, my monitor runs fine at 1440x900. Unless the driver installation messes up the resolution for some reason, there shouldn't be a problem. I have a acer widescreen LCD monitor and it supports a pretty wide array of resolutions.

Is there any way I can check if it's setting a strange resolution?

---

### Post by Vunutus on 2008-12-13
Bump. I'd really like to have working 3D in Ubuntu so I can run some games in Wine and have Compiz effects.

---

### Post by Vunutus on 2008-12-14
Bump #2

---

### Post by Vunutus on 2008-12-15
Bump again. I can't find anything helpful searching, hopefully somebody knows?

---

### Post by Shhnap on 2008-12-15
Ok, I gotta be honest with you. That's one weird bug and I don't really know what's going on. However, I would suggest a useful scrpit that can be found here: [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

It runs checks to see what is preventing your system from running compiz. Maybe it will help you pinpoint your error.

Hope it helps.

---

### Post by CatKiller on 2008-12-15
> **Vunutus said:**
> once I reboot, it goes to the Ubuntu progress bar then the video card shuts down completely, leaving nothing but a "No Signal Input" error on my monitor.

That isn't (probably) a resolution issue. It's more likely to be a refresh rate issue. Monitors can break (permanently) if they attempt to scan at a higher rate than they are physically capable of. One of the safeguards against this is to display nothing instead of attempting to scan faster than they physically can. There is a method (EDID) by which the monitor can announce the rates that it can handle, and the OS can adapt accordingly. Implementations of monitor, graphics card and graphics drivers can each be poor and break this method. NVidia's driver in particular seems to have a lackadaisical attitude to EDID.

Find the specifications for your monitor, and put the values in the "Monitor" section of your xorg.conf. For example, **mine** says this:

```
Section "Monitor"
        Identifier      "Eizo F77"
        Option          "DPMS"
        HorizSync       30-95
        VertRefresh     50-160
        DisplaySize     402 300
        Gamma           1.15
EndSection

``` Put the values for **your** monitor in **your** xorg.conf. I can't stress this enough. See above. The numbers you're interested in are HorizSync and VertRefresh.

It might be that the X server is getting erroneous EDID values. It might choose to use these rather than the values you've specified above. You can tell the X server to only use these values rather than any EDID numbers that it's been given by putting the following into your "Device" section.

```
        Option          "UseEDID"                       "False"

```

> **Vunutus said:**
> Is there any way I can check if it's setting a strange resolution?

The log file for your X server should tell you what choices it's made for valid modes, and which mode it has chosen to use. You can read the log file with ```
less /var/log/Xorg.0.log
```

(PageUp & PageDown do the obvious, and q will take you back to the command line)

---

### Post by Vunutus on 2008-12-15
Thanks for the informative post, I was in the midst of tinkering with my xorg.conf file when I realized the actual problem and it's somewhat embarrassing.

I neglected to mention the fact that I have a second monitor because I didn't think it was relevant. It's just an old CRT that I have sitting on my desk only for use when I really need the extra display space. A large majority of the time, it is turned off. I finished editing my xorg.conf and rebooted so it would be loaded in. To my dismay, the same problem presented itself. Before I rebooted to reset my xorg configuration, I looked over at my monitor and figured I would turn it on to see if it displayed anything at all. As it turns on, surprisingly, I see my login screen on it. With a little more tinkering around, I found out that the new driver apparently swaps which monitor head on my card registers as the primary monitor, causing my previously primary display to go blank (giving me the "no signal input" error) and shift everything onto my powered down CRT. I unplugged the CRT from my video card and everything works fine now (including compiz). :lolflag:

---

