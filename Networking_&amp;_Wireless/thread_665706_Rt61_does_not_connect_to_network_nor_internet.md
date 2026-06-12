---
title: "Rt61 does not connect to network nor internet"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by udoko on 2008-01-12
Studied and finally installed 7.10 dual booting onto a Vista machine. Checked compatibility list and bought an MSI PC 60G wireless adapter. Works better than my D-link DWA-552 on Vista. Ubuntu sees the adapter but I can not ping the network nor can I connect to the internet. I only used the network manager to configure the wireless connection just as in Vista but no luck. With Vista after plugging in this adapter and turning on the machine it found the device, loaded the drivers and I was connected. Maybe somebody has an easy way to configure the options. I have to swap back and forth in order to read the forum, the restart button is getting slightly worn.
Thanks

---

### Post by udoko on 2008-01-13
Since I could not get the adapter to work I uninstalled 7.10. Curiosity got the better of me and I ran the live CD of 8.04 Alpha3. The adapter saw four networks right away and I was able to connect easily after inputting the Wep key. Amazing. Just like Vista. Then I installed 8.04 to the hard drive and unfortunately after signing in I was left with a blank screen. Subsequently I uninstalled 8.04 and will stick with Vista until a somewhat more user friendly Linux is out there. My system was put togethe rby myself, has a Vista performance rating of 5.3 and since first boot two months ago have not had a BSOD. I like to fiddle around but not beat my head against the wall.
Thanks to whoever looked at my posts.

---

### Post by rustybronco on 2008-01-13
run the live cd and try it, i'm using 7.10 with the same chipset (pcmcia ) and it's working fine.

---

### Post by udoko on 2008-01-14
Thanks for the encouragement. I tried live CD of 7.10 again and golly gee the wireless network works. Will proceed and install Ubuntu 7.10.
Thanks again
Will let you know once I installed 7.10
udoko

---

### Post by rustybronco on 2008-01-14
If you have problems with network manager and dropped connections, try wicd [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by udoko on 2008-01-14
Installed on hard drive, had trouble using restricted driver for my high tech ATI card so I had to back out and reinstall. Vista side is running 1680x1050 with a Samsung2220wm. Ubuntu is running 1280x1024, which is ok. Can't use the restricted driver, it messes up the display to 800x600.
But the main thing is the wirelee is working. This is really the most important part of using a computer these days.
Thanks again

---

### Post by rustybronco on 2008-01-14
I haven't done it with 7.10, but with 7.04 you could issue in the terminal... modeline 1680x1050@(your refresh rate "60-65-70-75-whatever"-you MUSTcheck the monitor manual for the correct rate) then put the output of the command in monitor section of your xorg.conf file.
such as the thread [http://ubuntuforums.org/showthread.php?p=3756959#post3756959](http://ubuntuforums.org/showthread.php?p=3756959#post3756959)
or you could try to use a different driver such as "vesa" instead of the ati or radeon.
I bought a nvidia card so I don't have to put up with that cr#p.

---

