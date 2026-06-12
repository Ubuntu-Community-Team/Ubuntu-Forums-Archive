---
title: "Monitor/Dual Display issues"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by noahsias on 2011-02-16
Hello everyone,

I am new to the forums and semi-new to Linux/Ubuntu so please be patient with my newbie-ness. I'll try keep it to a low roar as much as I can.

I recently acquired a Sony Vaio VGN-NR430E from a friend who was upgrading to a new machine. Prior to reformatting it, it had at least 2 distros (Ubuntu and Xubuntu) installed on it, both fully functional with the Vaio's hardware.

Once I reformatted it, I went to plug in the Vaio via VGA to my Samsung SyncMaster 2333HD display. I went to switch the display to the VGA connection but it was grayed out. I rebooted the machine with everything plugged in and the display recognized the VGA connection. Once it starts loading Ubuntu.....connection lost and I'm back to square one.

I went into monitor settings and to my surprise, it recognizes the monitor. I can manipulate settings for both mirroring the display and for setting up dual monitors. Still, no recognition from the SyncMaster 2333HD.

So I come to you fine folks for some guidance. I've looked around various sites and forums for solutions and none have been helpful or right for my situation.

So recapping my setup:
Ubuntu 10.10
Sony Vaio VGN-NR430E (I believe it has an Intel GMA x3100 in it)
VGA connection into a Samsung SyncMaster 2333HD

Thanks for your time!
-Noah

---

### Post by sydbat on 2011-02-16
> **noahsias said:**
> Hello everyone,

I am new to the forums and semi-new to Linux/Ubuntu so please be patient with my newbie-ness. I'll try keep it to a low roar as much as I can.

I recently acquired a Sony Vaio VGN-NR430E from a friend who was upgrading to a new machine. Prior to reformatting it, it had at least 2 distros (Ubuntu and Xubuntu) installed on it, both fully functional with the Vaio's hardware.

Once I reformatted it, I went to plug in the Vaio via VGA to my Samsung SyncMaster 2333HD display. I went to switch the display to the VGA connection but it was grayed out. I rebooted the machine with everything plugged in and the display recognized the VGA connection. Once it starts loading Ubuntu.....connection lost and I'm back to square one.

I went into monitor settings and to my surprise, it recognizes the monitor. I can manipulate settings for both mirroring the display and for setting up dual monitors. Still, no recognition from the SyncMaster 2333HD.

So I come to you fine folks for some guidance. I've looked around various sites and forums for solutions and none have been helpful or right for my situation.

So recapping my setup:
Ubuntu 10.10
Sony Vaio VGN-NR430E (I believe it has an Intel GMA x3100 in it)
VGA connection into a Samsung SyncMaster 2333HD

Thanks for your time!
-NoahWelcome to the UF.

If the 2 distros were working perfectly, why did you reformat? 

I suspect that your friend had everything set up well and since you formatted, you will have to install some little thing that always gets installed, but we never really remember what it is until we need it. I hope that makes sense.

Have you checked to make sure that any "Restricted Drivers" are installed? I do not think there are any, but it is good to check.

---

### Post by noahsias on 2011-02-16
> **sydbat said:**
> Welcome to the UF.

If the 2 distros were working perfectly, why did you reformat? 

I suspect that your friend had everything set up well and since you formatted, you will have to install some little thing that always gets installed, but we never really remember what it is until we need it. I hope that makes sense.

Have you checked to make sure that any "Restricted Drivers" are installed? I do not think there are any, but it is good to check.

I reformatted for a fresh start on everything and wanted 10.10 installed. Also, I did the bulk of his installing and troubleshooting when he owned it since he is fairly tech illiterate. To my knowledge, he had absolutely no issues with getting it to work with external displays "out of the box". I also should mention that I meant that he had 2 distros installed collectively on his machine, not together. Also, the most current one was Xubuntu 9.something. He had Ubuntu 9.something before and had no issues with monitors too.

Fairly confident that there are no restricted drivers to install. I would check that via Synaptic Package Manager yes?

---

### Post by sydbat on 2011-02-16
> **noahsias said:**
> I reformatted for a fresh start on everything and wanted 10.10 installed. Also, I did the bulk of his installing and troubleshooting when he owned it since he is fairly tech illiterate. To my knowledge, he had absolutely no issues with getting it to work with external displays "out of the box". I also should mention that I meant that he had 2 distros installed collectively on his machine, not together. Also, the most current one was Xubuntu 9.something. He had Ubuntu 9.something before and had no issues with monitors too.

Fairly confident that there are no restricted drivers to install. **I would check that via Synaptic Package Manager yes?**No. You need to go to System > Administration > Hardware Drivers (the exact names may have changed in 10.10).

It could also be that your graphics are no longer supported under 10.10, which could explain the difficulty.

---

### Post by noahsias on 2011-02-16
> **sydbat said:**
> No. You need to go to System > Administration > Hardware Drivers (the exact names may have changed in 10.10).

It could also be that your graphics are no longer supported under 10.10, which could explain the difficulty.

I went to Additional Drivers and nothing came up. I guess I'll try 10.04 and see where it takes me. I'll report back when I get more details.

Appreciate the help.

---

### Post by noahsias on 2011-02-16
Installed 10.04 and still the same results. Checked Hardware Drivers and there were none to be found. I'm puzzled. I have another machine, a tower, running 10.10 and it has no issues with my monitor.

I'm going to try the Vaio on another monitor to see if anything changes.

---

### Post by noahsias on 2011-02-16
........so I'm typing this from my 40 inch Samsung TV. The Vaio works without a hitch on this display. So I think there must be some incompatibility issues with my Samsung monitor and this Vaio.

You'd figure if it works on one Samsung it would work on another?

Still would like to troubleshoot this though if possible.

---

### Post by jwcalla on 2011-02-16
What adapter are you using with your TV?  HDMI, DVI, VGA?

---

### Post by noahsias on 2011-02-16
> **jwcalla said:**
> what adapter are you using with your tv?  Hdmi, dvi, vga?

vga

---

### Post by coolwhipdefuser on 2011-02-16
Could it have anything to do with the refresh rate on the monitor vs. what your TV is compatible with? I've seen lots of issues in the past on Windows platforms.

---

### Post by jwcalla on 2011-02-16
> **coolwhipdefuser said:**
> Could it have anything to do with the refresh rate on the monitor vs. what your TV is compatible with? I've seen lots of issues in the past on Windows platforms.

I agree.  I am seeing a lot of questions like this on this forum, too.  It seems to be a common issue (a monitor isn't coming on, or the resolution isn't right, etc.).  Is there a clearly-defined method to getting this to work?

I had a similar problem with my second monitor.  I couldn't get it to come on (or, if it came on, the resolution was too low -- I forget).  I had to go to the mfr's website and find the HorizSync and VertRefresh frequencies (these are stored in the Windows driver file), and the desired resolution and enter them manually into my xorg.conf file.  I use a VGA adapter for this second monitor so the monitor can not identify itself and its properties to the video card.  I remember that I could not get the right resolution until I found the correct HS and VR numbers.

---

