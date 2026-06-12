---
title: "Driver Woes"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by Ericj1186 on 2009-05-15
All right, I decided after my issues with 9.04 (see other topic) to revert to 8.04.  I was able to actually get a lot more done here, but I ran into some critical issues.

First one guide I read on going SLi said to remove my bridge before doing it otherwise I will get black screened.  I did that and installed Ubuntu 8.04 to positive results.  So, I went to the IRC channel for Ubuntu where they told me how to install my drivers.  I cannot do ctrl + alt + F2 to boot my Nvidia driver for some reason, so I went with going with the sound card first.  

I move the sound card drivers to my desktop, Cd'd to it.  I then ran sudo make and sudo make install (per the readme).  I rebooted, and now, it loads a black screen that says "Loading Hardware drivers" and that process fails, then it hangs on Loading Drivers Manually forever.  Also, after doing this update, the Ubuntu load bar takes A LOT longer.  I go back to the IRC chat and one person suggested that I have the wrong kernel version.  [http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html) - I used that site to find my creative X-Fi drivers, but it doesn't list kernel version.

My questions are is there A. a way to reverse what I did with the driver, and B. a way to find definite drivers?


Edit:  I saw this: [http://ubuntuforums.org/showthread.php?t=870001&highlight=Creative+Sound+Blaster](http://ubuntuforums.org/showthread.php?t=870001&highlight=Creative+Sound+Blaster)
It mentions Ubuntu 9.04, but will it still work with my version?  Also, is there a guide like this for setting up Nvidia?  I am using two Geforce 250 GTS, but before I go SLi, I figured, I should upgrade the drivers on them separately/not bridged together.  Is this a good idea?

---

### Post by Ericj1186 on 2009-05-16
Can anyone help me with this?

I went into the IRC chat, we ran the Nvidia drivers from their site, rebooted the computer, and it loaded back into the terminal/tty1.  It wouldn't go back to the GUI until I uninstalled the driver.

Can someone please help me out?

---

