---
title: "brightness problem"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by Griffiss on 2010-10-05
Hi everyone

I have a problem adjusting brightness on Lucid. I've tried a few of the solutions for similar problems that I've found on here but none have worked so far.

My laptop is a Samsung R510, with onboard graphics
lspci gives: ```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

I can't adjust the brightness with the panel applet, with the power managment sliders, nor with smartdimmer. smartdimmer gives output: ```
init_nvclock() failed!
```

I tried to use Kamal's fix here: [https://launchpad.net/~kamalmostafa/+archive/linux-test-i915bri/+build/1856596](https://launchpad.net/~kamalmostafa/+archive/linux-test-i915bri/+build/1856596)

but this didn't work. Perhaps I did something wrong, I'm not sure what I'm doing with this type of thing.

Any help with this would be great. My retinas will thank you!!!

---

### Post by NightwishFan on 2010-10-05
Boot with these parameters:
```
acpi_backlight=vendor i915.powersave=0
```

Do you know how to add boot options? If not I will explain how to do it temporarily and permanently if it works.

Note: i915.powersave=0 is only needed if you see an odd flicker on the screen every once in a while.

---

### Post by jtarin on 2010-10-05
I know this is a problem on many computers....sometimes there isn't a solution but I use this application [F.lux]("http://www.stereopsis.com/flux/") on three computers and really like it.While not specific to adjusting brightness maybe it will overcome your problem if you change some of the parameters that it workd with. The Linux download has an Ubuntu 10.04 ppa available.

---

### Post by Griffiss on 2010-10-05
@NightwishFan

I tried adding 'acpi_backlight=vendor' to the /etc/default/grub file so that one of the lines looked like this:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
```

Then updated grub and rebooted. Is this what you meant by adding boot options? This didn't work either. In fact now the brightness applet icon tells me it cannot get laptop panel brightness. So at least it's being more honest :)

@jtarin: thanks for your help. I'd prefer a specific fix for this problem. I would like to learn more about why it's happening and so on. I'm sure there's some way of adjusting what's already there so that it works. If not though, I'll try your solution.

---

### Post by NightwishFan on 2010-10-05
Odd, I have this same device and it works. Has to be something else than just the video driver. That is the only fix I know. Sorry I could not be of more help. :(

---

### Post by jtarin on 2010-10-05
> **Griffiss said:**
> 
@jtarin: thanks for your help. I'd prefer a specific fix for this problem. I would like to learn more about why it's happening and so on. I'm sure there's some way of adjusting what's already there so that it works. If not though, I'll try your solution.Just trying to minimize your pain. :)

---

### Post by Griffiss on 2010-10-05
:) ok thanks. But in fact I've tried it now and it also doesn't fix the problem. The brightness dips and reddens for a fraction of a second then goes back to normal :(

One other symptom that might point to a solution is that after I try to use the function keys to adjust the brightness, the keyboard no longer works and I have to reboot!

---

### Post by NightwishFan on 2010-10-05
After trying to do the brightness check your logs for stuff or post the output of the command dmesg. (It might complicate this since your keyboard locks up. :/)

---

### Post by jtarin on 2010-10-05
[Here's a fix]("http://www.ubuntugeek.com/fix-your-laptops-brightness-function-keys-operating-properly-in-hardy.html") for Hardy using two scripts. While not for Lucid specifically...could work.

---

### Post by Griffiss on 2010-10-05
Ok, I would like to do that but I don't know how I can post the output without the keyboard working at all. I thought I could just copy-paste but it seems the right mouse button is also affected by whatever's going on here, so I can't get the drop-down menu with the copy option to appear either. Also, the main menu button on the panel stops working. This is quite bizarre behaviour - a real bug

---

### Post by NightwishFan on 2010-10-05
I would report a bug about the kernel.
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Meanwhile, perhaps also open the file /var/log/syslog, save it as a syslog.txt on your desktop and upload here. I will take a look.

---

### Post by Griffiss on 2010-10-05
@jtarin, unfortunately that didn't work either.

@NightwishFan, I can't attach the file because it exceeds the forum size limit for this file type. I have to go now though. Thanks a lot for your help with this guys. I have to go now but I'll check back tomorrow. Any suggestions are very welcome!!!

---

### Post by NightwishFan on 2010-10-05
Sure. I hope you get it working. If you want to attach the log first bzip compress it.

---

### Post by Griffiss on 2010-10-06
Ok, I attached syslog as a zip. I have no clue what any of it means. I'll file a bug report now also. Thanks for the advice.

---

### Post by Griffiss on 2010-10-06
Well, I found a workaround, by using ```
sudo setpci -s 00:02.0 F4.B=70
``` where B=00 to FF, for black to bright respectively. And 00:02.0 is the address of my graphics controller given by lspci.

Found here: [http://ubuntuforums.org/showthread.php?t=1570218](http://ubuntuforums.org/showthread.php?t=1570218)

Which got it from here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/538256](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/538256)

Which got it from here: [https://bbs.archlinux.org/viewtopic.php?id=73889](https://bbs.archlinux.org/viewtopic.php?id=73889)

So I have a way to control my brightness now!!!

However, all the dysfunction of the function keys and the applet is still a problem

---

### Post by devian50 on 2011-01-04
> **Griffiss said:**
> Ok, I would like to do that but I don't know how I can post the output without the keyboard working at all. I thought I could just copy-paste but it seems the right mouse button is also affected by whatever's going on here, so I can't get the drop-down menu with the copy option to appear either. Also, the main menu button on the panel stops working. This is quite bizarre behaviour - a real bug

Hey have you tried hibernating? you said the keyboard locks up until you reboot but try hibertating. it shuts down the computer but keeps what you were doing in memory! try this out!

BTW i have a problem sorta like this but when i press my Fn+left or right to increast or decrase the brightness it gives me a little popup for the brightness but nothing happens! I have tried the power management and i have tried smartbrightness (or whatever its called) and i have even edited the brightness cfg file! but nothing! im using an Acer laptop with an Intel HD gfx card and an i5 64bit processor if that makes a difference.

im running Ubuntu 10.10 btw!:-x

---

