---
title: "I can't switch to Ubuntu because..."
date: 2009-05-29
forum: New to Ubuntu
---

### Post by Gp. on 2009-05-29
1. My Logitech Quickcam Pro 9000 works, but I can't adjust any settings for it. (Like turning of rightlight!)

Everyone like oh yeah look around, I have. Nobody can help me with this.

2. The Soft reset bug in the kernal alot of people are getting, I have it if I even try to turn my IDE/SATA on in the bios.

3. My Brother HL-2140 printer is a pain in the *** to install on Ubuntu. I still haven't got it working.

If anyone knows how to solve these with ease, goodbye Windows!

---

### Post by Bölvaður on 2009-05-29
Be patient.

In few years when you have a new computer, the webcam has been lost/broken for months and you dont like with your brother any more or he has a new printer. Then you will probably not have to deal with these issues because it is getting easier to get hardware working, and because then you might know what hardware works for linux before you buy :)

---

### Post by LowSky on 2009-05-29
I have the soft rest bug and it isn't affecting my use of Ubuntu.
Bölvaður, Brother is a printer brand....lol, I found instructions here
[http://openprinting.org/show_printer.cgi?recnum=Brother-HL-2140](http://openprinting.org/show_printer.cgi?recnum=Brother-HL-2140)
as for the webcam and for any equipment, you have to realize that Linux is not Windows, The Linux community is not responsible for these devices the manufacturers are. If you wan the thing to use all its features, then ask the company to supply linux software and drivers.
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by Hospadar on 2009-05-29
Depending on how hard you want to use linux, you migh consider just using a windows vm for all your device problems.

Unless you are constantly printing and webcamming, I don't think (for me at least) that it would be a problem to use those things through a vm

For example, go to sun's website, get their repository for virtualbox, install their version, install a windows VM (Virtual Machine, super easy), forward your usb devices that you want to use (assuming they are USB), install the drivers in the windows VM, and then you can use your devices in windows (VM) while you wait for linux support to catch up.

That said, if there's a lot of stuff you need in linux and you can't make it work, just don't use linux, there's no sense in using an OS that just doesn't do what you need it to do.  I'm all for sticking it to the MS man, but not at the cost of being able to do what I need to do.  Wait a couple release cycles, and probably your hardware will be supported, and all will be well, but in the meantime, use what works, if that means a VM or real windows installation, than so be it.  You can always dual boot too.

Here's the link to sun's virtualbox site:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

There is an open source version of virtualbox (both versions are free as in money though) but only the non-open source version has usb support.

---

### Post by billgoldberg on 2009-05-29
> **Gp. said:**
> 1. My Logitech Quickcam Pro 9000 works, but I can't adjust any settings for it. (Like turning of rightlight!)

Everyone like oh yeah look around, I have. Nobody can help me with this.

2. The Soft reset bug in the kernal alot of people are getting, I have it if I even try to turn my IDE/SATA on in the bios.

3. My Brother HL-2140 printer is a pain in the *** to install on Ubuntu. I still haven't got it working.

If anyone knows how to solve these with ease, goodbye Windows!

There is a good guide on installing brother printers here:
[http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793)

It worked for mine.

I also get the softreset error ever since I installed a second hdd, but I don't notice any wrong behavior, everything works. If it bothers you, check the launchpad bug report, there might be fixes posted.

---

### Post by TheLions on 2009-05-29
> **Gp. said:**
> 

3. My Brother HL-2140 printer is a pain in the *** to install on Ubuntu. I still haven't got it working.

If anyone knows how to solve these with ease, goodbye Windows!

did you even check manufacturers page?

i did: [http://solutions.brother.com/linux/en_us/download_prn.html#HL-2140](http://solutions.brother.com/linux/en_us/download_prn.html#HL-2140)

---

### Post by albinootje on 2009-05-29
> **Gp. said:**
> 
3. My Brother HL-2140 printer is a pain in the *** to install on Ubuntu. I still haven't got it working.

Which Ubuntu release are you using ?
Here's people with a possible solution :
[http://ubuntuforums.org/showthread.php?t=987865](http://ubuntuforums.org/showthread.php?t=987865)

---

### Post by ajaysutton on 2009-05-29
In my own migration from Windows to Linux, I've found a couple of small things like you mentioned, but found that the rewards reaped from overcoming those changes have been well worth it.  I had to change printers, and leave behind an external burner that I'd used for years, but all the changes that have been "forced" on me have been good changes that have made me move forward.

A. Jay

---

### Post by meho_r on 2009-05-29
> **Gp. said:**
> 1. My Logitech Quickcam Pro 9000 works, but I can't adjust any settings for it. (Like turning of rightlight!)


Did you try installing xawtv package and then setting, e.g., exposure with the command: ```
v4l2ctl -c /dev/video1 setattr Exposure 900
```

I tested it on my Logitech Quickcam (not Pro) and it worked.

---

### Post by Gp. on 2009-06-05
I just did then, command not found?

---

