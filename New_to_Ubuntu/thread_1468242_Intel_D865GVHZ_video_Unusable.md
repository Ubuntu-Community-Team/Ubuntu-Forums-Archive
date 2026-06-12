---
title: "Intel D865GVHZ video Unusable"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by KD8ENK on 2010-05-01
HI I have an Intel D865GVHZ mother board that I am trying to dual boot with Ubuntu 8.04 so I can use the EMC2 software. The problem I am having is that the video is so bad that I can not use it in this way. Is there a way to load a driver of some sort or is there a way to change the resolution so that it is manageable. If you open a window the complete window is not accessible as the bottom is cut off.  Any help will be appreciated thanks 

    Oh by the way I am a newbie to linux so I need the easy version to a fix if there is one.

---

### Post by anewguy on 2010-05-01
I am not familiar with the 865 chipset, but I did a Yahoo! search using ubuntu 8.04 intel 865 graphics driver and came up with this link which I think you will find helpful.  If there is something there you don't understand or are not sure about, just post back here and we'll try to help you through it.

[http://packages.ubuntu.com/hardy/xserver-xorg-video-intel]("http://packages.ubuntu.com/hardy/xserver-xorg-video-intel")

Dave :

---

### Post by gordintoronto on 2010-05-01
Here's a trick which might help a little bit: if you hold down the Alt key and the left mouse button, you can move a window without having to be at a border.

It sounds like your computer is running with a low resolution setting. 
Can you run Preferences/Display to see what it is?

---

### Post by KD8ENK on 2010-05-01
Thanks for getting back to me so quick. I downloaded the drivers and it said that the latest were already installed. Just setting here I thought I would try another monitor. I was using an ACER AL1511 so I hooked up an ACER AL2223W and it works perfect the color is great and was bad before everything is just working great now. So the next question is why the difference in the monitors and is there a way to fix that?

---

### Post by anewguy on 2010-05-01
Well, I'm not sure why it would make a difference unless the 1st monitor didn't identify itself to Ubuntu and therefore you got a low-res generic monitor definition.  The 2nd monitor probably was able to identify itself to Ubuntu (refresh rates, max resolutions, etc.) and that's why it probably worked.

You could check by trying the following:

- with the monitor that works plugged in (I assume it is now), go to System/Preferences/Monitors and see if it lists the monitor on the screen.

- now, you'll need to go back to the 1st monitor, so shutdown, switch monitors and power back up.  Do the same thing again as above and you'll probably find the monitor isn't identified.


That's my guess - not sure.

Dave ;)

---

### Post by KD8ENK on 2010-05-01
I did a little searching and found this 
[https://wiki.ubuntu.com/X/Troubleshooting/Resolution#Problem:%20%20Resolution%20with%20Intel%20graphics%20was%20correct%20in%20Intrepid%20or%20Jaunty%20%28with%20no%20xorg.conf%20configuration%29%20but%20is%20limited%20in%20Karmic](https://wiki.ubuntu.com/X/Troubleshooting/Resolution#Problem:%20%20Resolution%20with%20Intel%20graphics%20was%20correct%20in%20Intrepid%20or%20Jaunty%20%28with%20no%20xorg.conf%20configuration%29%20but%20is%20limited%20in%20Karmic)
 
I will give it a shot tomorrow.

---

### Post by gordintoronto on 2010-05-01
You might also Google:
nomodeset grub linux 

I think "anewguy" nailed the explanation for why it happened, and I think "nomodeset" is the key to stop it from happening.

---

### Post by KD8ENK on 2010-05-02
I did what anewguy suggested and check out what the 22 in Acer had then plugged in the 15 in Acer the setting were set to the lowest resolution. I changed it to the highest and had to use the tab button 4 times to get to the apply button (counted that while the other monitor was still plugged in) and she works like a charm. The only other problem is during boot up and shut down I get “input not supported”  and the resolution is real low for the login screen but that is not a big deal as it is working and I can read the display after the boot up is done.

---

### Post by anewguy on 2010-05-02
I'm just glad you found a solution that is acceptable to you.  I haven't done a search myself, but you may want to try searching the forum to see if there are any references to the login screen being in a low resolution and if there are any suggestions for modifying it.

Good work!

Dave ;)

---

