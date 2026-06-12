---
title: "Configuring external monitor for laptop"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by mvalviar on 2010-10-09
Hello,

I'm a newbie when I comes to hardware so please bear with me.

I have a laptop with nvdia geforce 310M and a 14"/16:9 display and a Hans-G HW191 19"/16:9 monitor. I want to try a number of things. But first I need to have the nvdia settings gui to detect my external monitor properly. 

It is being detected as crt-0 on gpu-0 with a max resolution of 1024x768 (the external monitor has a max resolution of 1440x900). How do I get it detected properly?

---

### Post by TeoBigusGeekus on 2010-10-09
Have you installed any restricted drivers for your card?

---

### Post by irv on 2010-10-09
> **TeoBigusGeekus said:**
> Have you installed any restricted drivers for your card?

I believe you have something here. I have the same monitor and have problems when I run with it connected to my laptop which uses a restricted driver. But when I hook this same monitor up to my desktop it works fine.
My problem is I only get a half a screen until I change the setting on the monitor itself. If I then use the hot keys to switch to the external monitor only I get a good resolution but have to adjust the setting again on the monitor to get a full screen. I am starting to believe it is a combination of restricted driver and the monitor. If I use a different monitor I don't have this problem.

---

### Post by JohnHeikkila on 2010-10-09
Open "nvidia-settings" and try the settings

---

### Post by mvalviar on 2010-10-09
Yes, I have proprietary drivers. I don't know what version it is. I just says "(version current) [Recommended]." I did play around with nvidia-settings. I plug in the external monitor via a vga port on the laptop and I click detect displays and I get crt-0 on the resolution drop down I don't see 1440x900 (the external monitors max resolution). I have ubuntu on a desktop as well. When I connect the monitor there it is detected as a hans-g and the appropriate resolution is automatically selected.

---

### Post by mvalviar on 2010-10-11
bump

---

### Post by bcurry on 2010-10-12
> **mvalviar said:**
> Yes, I have proprietary drivers. I don't know what version it is. I just says "(version current) [Recommended]." I did play around with nvidia-settings. I plug in the external monitor via a vga port on the laptop and I click detect displays and I get crt-0 on the resolution drop down I don't see 1440x900 (the external monitors max resolution). I have ubuntu on a desktop as well. When I connect the monitor there it is detected as a hans-g and the appropriate resolution is automatically selected.

It seems like I'm having approximately the same problem with my nvidia card on my HP Laptop.  I just installed 10.10 32-bit (not upgrade) from 10.04 64-bit and my ViewSonic LCD (1680x1050) has a max resolution in nvida-settings of 1360x768.

Everything worked great on 10.04 64-bit so I'm downloading 10.10 64-bit to see if that helps.

I've played around with nvidia-settings and my xorg.conf to no avail.  I used to build my own xorg file but so many things have changed since I did that I'm kinda' lost trying that now.

Cross your fingers.

:)

---

### Post by ft-Orchard on 2010-10-12
You guys should try the following guide. It's not particularity for Ubuntu, but I guess it should do.
Make sure you back-up all the files.

[http://wiki.archlinux.org/index.php/Xorg#Monitor_settings](http://wiki.archlinux.org/index.php/Xorg#Monitor_settings)

---

### Post by mvalviar on 2010-10-12
> **ft-Orchard said:**
> You guys should try the following guide. It's not particularity for Ubuntu, but I guess it should do.
Make sure you back-up all the files.

[http://wiki.archlinux.org/index.php/Xorg#Monitor_settings](http://wiki.archlinux.org/index.php/Xorg#Monitor_settings)

Too time consuming for me to follow. I think I'll try 10.10 to see if it works somehow.

---

### Post by mvalviar on 2010-10-13
bump

---

### Post by irv on 2010-10-13
> **mvalviar said:**
> bump

Your last post you said you were going to try 10.10? Did you do that? and how did it work if did?

---

### Post by craytor on 2010-10-14
I just installed Ubuntu 10.10 on my toshiba tecra laptop. I use a Samsung 930b external monitor. Ubuntu only uses 2/3 of the monitor space. I've tried installing a driver, but it is not compatible with Ubuntu. Any suggestion on how to get my external monitor to work with Ubuntu? I am a beginner with Ubuntu and open source. 

Thanks,
Chuck

---

### Post by irv on 2010-10-14
> **craytor said:**
> I just installed Ubuntu 10.10 on my toshiba tecra laptop. I use a Samsung 930b external monitor. Ubuntu only uses 2/3 of the monitor space. I've tried installing a driver, but it is not compatible with Ubuntu. Any suggestion on how to get my external monitor to work with Ubuntu? I am a beginner with Ubuntu and open source. 

Thanks,
Chuck

I have a Hans-G 22" Monitor I use with my desktop and on occasion use with my Dell Inspiron 1521 laptop. Not all the time, but once in awhile it will boot up with just a half screen and sometimes with a small piece of the display way to one side. What I need to do is go into setup on the monitor and get to the setting where I can do an auto refresh, and the monitor with reset itself to the full screen. There is no way to keep the monitor on this setting to do this at power up. Ever so often I need to do this with the desktop and the laptop. It doesn't do this in windows just Ubuntu Linux. I even had Peppermint Linux on one of the computers and it never did it with that OS.  I am not sure if it is a combination of the monitor model and Ubuntu or what. I don't use the monitor that much so I just put up with it. I have another monitor/TV flat panel that work without any problem. 
By the way it did it with 9.04, 9.10, 10.04, and 10.10 version also.

---

### Post by huzzak on 2010-10-16
> **craytor said:**
> Ubuntu only uses 2/3 of the monitor space.

I think your problem is similar to the one I have described [here]("http://ubuntuforums.org/showthread.php?t=1595620").  It seems to be a problem with the virtual screen on which the monitors are overlain.  I used the arandr tool to try to configure things and it exposed the lighter gray box pointed out by the red arrow in the picture below.

[IMG]http://img.photobucket.com/albums/v101/Huzzak/scr_layout.png[/IMG]

When I set my monitors to be the full resolution possible they are cutoff and the rest of the screen is black in relation to how the square is in the screen.  Similar, I think to your 2/3 monitor space problem.

I'm not sure but I think if we can figure out how to change the size of the inner light gray box we'll be able to fix our problems.  Any ideas?

---

### Post by huzzak on 2010-10-20
If you are indeed having the same problem as me, salvation is nigh!  [Click here!]("http://ubuntuforums.org/showthread.php?t=1595620")

---

### Post by mvalviar on 2010-11-25
I tried booting to 10.10 and the monitor is still being detected as CRT

---

### Post by mvalviar on 2010-12-07
Should I install 10.10 then install the nvidia driver?

I thought that booting to 10.10 and configuring the monitor (with out proprietary drivers) would be enough. On 10.10 display config dialog the monitor is still being detected as crt-0.

Would installing 10.10 and installing the nvdia driver fix this issue?

---

### Post by mvalviar on 2010-12-07
Maybe I'm asking for something that is not possible. What I'm trying to is have have cloned video output on the laptop's display and the external monitor. Also I'd like to put the external monitor at it's max resolution of 1440x900 and the laptop display at 1366x768. Is this possible?

---

### Post by mvalviar on 2010-12-08
bump

---

