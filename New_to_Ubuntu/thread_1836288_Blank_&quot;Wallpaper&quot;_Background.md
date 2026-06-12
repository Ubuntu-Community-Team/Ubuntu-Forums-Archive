---
title: "Blank &quot;Wallpaper&quot; Background"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by jamoore1 on 2011-08-30
I have just installed Ubuntu for the first time a couple of days ago. I am using a Toshiba Satellite-P500 Series laptop. It's the big one with the 18.4 in screen. I have 2.1 ghz Centrino 2 dual core processor, 4GB DDR2 RAM, and discrete ATI M96 Mobility Radeon HD 4650 video card. I am running Ubuntu 11.04 x64 on a dual boot install with Windows Vista. The installation ran perfectly, I downloaded the iso and burned it to a CD, rebooted and installed through my boot selection menu. After installation completed (I ticked the box to download updates during install, but left off the proprietary software option after configuring my wifi) when I rebooted, I was greeted with my username and prompted for my password. After entering the password, my speakers play the little "Ubuntu start music", but all of my "icons" and such are gone, I only have a purple "wallpaper" on my screen. (Forgive the windows terms, I just don't know what everything is called yet). Also I do not know many keyboard shortcuts for Linux, but ctrl + alt + t does not cause a terminal to appear. I have found that I can press ctrl + alt + f5 and I get a terminal prompt for my username and password and after signing in I get the standard Linux command line me@cpuname:~$. For this reason I am lead to believe that I have a (mostly) healthy operating system running under the hood, but I am not sure what I should do to get graphical side going. Also, I have used the sudo  blah update command (can't remember exactly what) but a lot of updates failed to download (I think my wifi is no longer configured, and I don't know how do it with a terminal interface) and then the ones that did download (presumably during install) unpacked and installed themselves. The only other note is that I can press ctrl + alt + f7 to return to the blank "Wallpaper" view. Nothing I've thought to try has helped me and I don't know very much at all so some step by step instruction would be greatly appreciated if anyone has any idea what the problem is. If you need more information I will try to respond to your post promptly.

---

### Post by jtarin on 2011-08-30
If you can manage a hard wire connection for the install/updates etc; this would be best as Ubuntu might need to download a driver for your wireless card.

---

### Post by jamoore1 on 2011-08-30
Thank you for the tip. I can easily connect to the hardwire in my home, but I am far more concerned with why the rest of ubuntu isn't working.

---

### Post by jtarin on 2011-08-31
With a good connection try "sudo apt-get update" then see if your problems still exist after a reboot.

---

### Post by jtarin on 2011-08-31
If your upgrading from an earlier version of Ubuntu there is a drastic change in the 11.04 desktop. At the login screen choose the Gnome version to login in with and you will probably locate some icons and be a little more familiar.

---

