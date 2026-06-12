---
title: "Video Resolution and Keyboard Problem"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by Mid West Kevin on 2009-07-16
I'm completely new to ubuntu. My purpose in understanding ubuntu is to revitalize older x86 boxes to use in a Citrix XenApps environment. Dumb terminal concept, low overhead and re-cycle old equipment. My background is Microsoft, and Citrix ? I like what I see so far with ubuntu.
 
Anyhow; my installation of ubuntu 9.04 went smooth until I tired to adjust my display resolution. 800x600 was the new install and when I followed the great detailed instructions found throughout this site the resolution went to 640x480. Crazy ! I even downloaded the EnvyNG package and that didn't work. I downloaded an older version of ubuntu 8.04 to see if the resolution was different, I know it doesn't make complete sense. Resolution was still a problem.
 
Number pad on the keyboard didn't work in etiher installation.
 
What was happening on both installation of ubuntu is I use a "Blackbox Server Switch"; Monitor, Keyboard, Mouse plugin type box to use with 2 or more computer boxes. They are great for saving benchtop space. Normally; its fine and doesn't cause problems. For some reason the Server Switch causes problems in my applications of ubuntu 8.04 and 9.04.
 
When I connected my Monitor, Keyboard, and Mouse directly to the Ubuntu 9.04 or Ubuntu 8.04 boxes life became wonderful. Resolutions are adjustable, and keyboard is fully functional. I'm moving forward with my XenApp quest.
 
You guys have a great informative site, yall do a great job in sharing the information. I hope this post might shed so light on some of the video resolution problems that people are having.

---

### Post by jbrown96 on 2009-07-16
Video cards are able to query monitors (or in your case, the blackbox) to determine what resolutions are available. However, it doesn't just return the resolutions, it returns a EDID, which it looks like Ubuntu doesn't understand. You will need to set the resolution manually in your xorg.conf file. [Here's a good guide]("http://www.gentoo.org/doc/en/xorg-config.xml") to help you (skip to section 4: tweaking your Xorg). If you have an ATI or Nvidia graphics card, they both include a utility to set the resolution, and that will probably be easier starting out. Make sure your install the proprietary driver for these cards first (System-->Administration-->Hardware Drivers). The ATI utility is called Catalyst Control Center and should be located in your Applications menu. I'm not sure if the nvidia-settings program is installed or not; you can install it with ```
sudo apt-get install nvidia-settings
``` If you use the Nvidia app, try it once and see that it works, but the changes won't last. Alt+F2 then ```
gksu nvidia-settings
``` this will give the program "root" powers, so it can save your xorg.conf, and then just make sure to save the file before you exit.

---

### Post by Mid West Kevin on 2010-07-26
Thanks for your help.  I appreciate the information you provided.

Kevin

---

