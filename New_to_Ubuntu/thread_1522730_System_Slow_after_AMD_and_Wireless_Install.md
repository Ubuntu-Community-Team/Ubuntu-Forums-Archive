---
title: "System Slow after AMD and Wireless Install"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by Gusy on 2010-07-02
Hi. 

  I&#8217;m not completely inexperienced when it comes to Linux / Unix from a command line point of view, but I have very little day to day experience with a full blown modern graphical OS.

  I&#8217;ve set up a dual boot system with Windows XP and Linux Mint 9 (64 bit). I haven&#8217;t attempted to use Linux as a home OS in about ten years and wanted to see how well a modern, user-friendly distribution would work. I chose Linux Mint 9. Everything started fantastically. I was amazed at how sophisticated this was compared to distributions I had tried years ago.

  I&#8217;ve been adding software and testing for a few days.  Last night, I made two changes almost at the same time, and since then,  several things seem to be drastically slower.

  First, I attempted an install of my wireless adapter&#8217;s drivers using the Wireless Drivers utility. Second, I installed the AMD graphics driver from the 3rd party driver app.

  Since then, when I boot, the green screen stays up much much longer. When I log in, I get an error about Power Management failing to respond (and asking if I want to log out before I&#8217;ve logged in, if that makes sense). After that, several apps run very slowly or not at all. Firefox runs just fine. Asking the system to shut down takes minutes to show the options list. A terminal window takes minutes to appear. Firefox, on the other hand, comes up right away.

  I ran a &#8220;top&#8221; from the command line to check my CPU usage and there was no noticeable usage. Memory usage was fine too. I can&#8217;t even open the Wireless Drivers app anymore. It just hangs indefinitely. I&#8217;ve uninstalled the Graphics drivers and a few things seem faster, but most don&#8217;t.
  Is there any way I can undo what I did? I&#8217;m fine without the graphics or wireless drivers. I just want my speedy OS back to play with? Thank you in advance for any advice you can give me.

---

### Post by warfacegod on 2010-07-02
At a guess, I'd say it's the video driver. By AMD I assume you mean ATi. ATi has made some progress in their drivers over the last six months or so but they are still far from perfect. It's generally recommended that using the proprietary/3rd party drivers only be done on an as needed basis. Try switching back to the "Recommended" driver. Things should be back to normal.

---

### Post by lkjoel on 2010-07-02
Could you please give me some more info?
MHz or GHz and RAM.

---

### Post by Gusy on 2010-07-14
I apologize. I posted this thread just as we were packing to move to a new home and haven't had time since to update it.

These are my basic system specs, as you requested:

AMD Athlon 64 X2 2200MHz (11x200) 4200+
Asus M2R32-MVP
2048 MB DDR2-800 SDRAM
ATI Radeon HD 3850 (512MB)

This is what I did, as best as I can remember:

My Linux Mint was booting very quickly. I decided to see if I could enable support for my Netgear wireless USB device. At the same time, I also noticed that there was a feature to enable support for my graphics card. I did these at roughly the same time and immediately after, Mint / Ubuntu has been extremely slow. Here are the steps I did right before the problem surfaced:

First I went into Administration - Hardware Drivers (Configure Third Party and Proprietary Drivers) to see if my wireless device was listed. It was not, but my ATI card was listed as ATI/AMD Proprietary FGLRX Graphics Driver. I figured I might as well activate it since I was in there.

Immediately after that, without rebooting, I went to another app, Administration - Windows Wireless Drivers (listed as /usr/sbin/ndisgtk). This is supposedly capable of using the .ini and .sys files from the windows versions of your wireless drivers. I pointed it at the correct files for my Netgear WNDA3100.

After this, I rebooted Mint / Ubuntu. I immediately noticed problems. Mint used to boot in seconds, now it was taking minutes to give me a log in prompt. The graphics seemed glitchy as well. Once I entered my user name and password, it gave me an error that something called Power Manager was not responding, and would I like to continue logging out, even though I was actually logging in.

Since then, I've un-activated the ATI driver. Unfortunately, I can't even get back into the Windows Wireless Drivers app. It just hangs and I have to do a Force Quit to get out. Shutting down in Linux takes even longer than logging in, close to five minutes. It then shows me another error about Power Manager not responding.

Thank you in advance for any help you can give me.

---

### Post by Gusy on 2010-07-14
I managed to remove the wireless driver with **ndiswrapper -r** and everything is running speedy now. I've tried installing just about every version of the driver that I can find and each time it slows the system back to a crawl until I remove them. I guess I'm going to have to stick with a wire for now.

---

### Post by mapes12 on 2010-07-15
I had the same problem when using a windoze driver with ndiswrapper. In the end I installed a natively supported wifi adapter. These links may help if you go down this path:-

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28supported%29|%28wifi%29#head-e669905d73a32156274930398b3d3c3468508d45](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28supported%29|%28wifi%29#head-e669905d73a32156274930398b3d3c3468508d45)

[http://shop.linuxemporium.co.uk/hardware/hardware-wireless.html?SID=3fcfb6b6b399b9af75f9aa8147f82dac](http://shop.linuxemporium.co.uk/hardware/hardware-wireless.html?SID=3fcfb6b6b399b9af75f9aa8147f82dac)

---

### Post by Gusy on 2010-07-16
Thanks!

Mine doesn't have natively supported drivers. I guess next time I'll consider buying a device that does.

---

