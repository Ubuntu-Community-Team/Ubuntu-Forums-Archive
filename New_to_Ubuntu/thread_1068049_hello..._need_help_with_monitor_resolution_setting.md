---
title: "hello... need help with monitor resolution settings"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by Meow Mix on 2009-02-12
I just recently purchased an Everex gPC3 with Ubuntu 8.04 preinstalled and I need some assistance getting my monitor setup properly on it. My monitor is an Acer x163w 15.6" Widescreen with a native resolution of 1366x768. However, with the latest drivers for my nvidia graphics card, the max I can get it to display is 1280x768. I would like to get this display showing at its native resolution. 

After searching the web I did find a command I could enter at command line terminal to change resolutions. ```
gksudo displayconfig-gtk
```

With this I was able to select Generic LCD 1360x768. However the max resolution it would allow is 1280x768. If I select plug and play, the max resolution allowed is 640x480. When I looked under the Acer category I could not find my particular model display so that is why I had to select generic LCD. I also downloaded and installed the latest nvidia drivers.

Can someone show me how to get the appropriate driver for my monitor set up so I can display it in its native 1366x768 resolution? Thanks.

---

### Post by BKonkle on 2009-02-12
Well, I know one way to try to solve this problem, but it's relatively advanced and might not be very easy for a newcomer to Linux.  I'll go ahead and throw this out there, but if anyone else knows an easier more beginner-friendly method, please jump in and help out.

From the terminal (Applications menu -> Accessories -> Terminal) you can enter the command:

```
sudo dpkg-reconfigure xserver-xorg
```

This will take you through a series of steps to configure your graphics system.  For most of these options, just press enter to accept the defaults.  You should come to a list of resolutions towards the end of the process, however, where you can choose which resolutions will be available.  Just make sure to select your desired resolution, and then finish up the rest of the process with the defaults.  If the resolution you are looking for is not listed there, then this solution is not going to work and you can go ahead and cancel the process with CTRL+C.

After that's all done, make sure all of your programs are closed press CTRL+ALT+Backspace to restart the graphics system without having to reboot your entire computer.  With any luck, your PC should be outputting at that native resolution now.

---

### Post by Meow Mix on 2009-02-12
Thank you, BKonkle.

After doing some more research and adding an appropriate modeline entry in the /etc/X11/xorg.conf file I was able to get it to display 1360x768. The native 1366x768 doesn't display properly. Some of the screen is cut off. Autoadjust on the monitor doesn't help. Could be an issue with the GeForce 6150SE-430 graphics chipset and/or driver.

However, when I run the monitor in 1360x768 the fonts look terrible. They look so terrible that I'm having to run it back in 1280x768 to view things decently.

I'm not an advanced linux user by any stretch but if I could get the fonts to render decently in the 1360x768 mode I would be very happy.

---

### Post by Phantoome on 2009-10-24
I'm had the same error,  and the same display so offcourse..
But i looked around on google and came to a thread of Ubuntu forum's (and also this one)
It helped me out and i don't have any problems with fkd up icon sets..

Here's the link,[URL="http://ubuntuforums.org/showthread.php?t=1045106"]
http://ubuntuforums.org/showthread.php?t=1045106[/URL]

Tought if it would help i would save other ppl lots of time!
~Phantoome

---

### Post by NCLI on 2009-10-24
Have you tried editing the resolution using nVidia's official tool?

---

