---
title: "x86 or x64? Graphics problems"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by zspace on 2009-01-03
I have been using ubuntu for a bit now and I just reinstalled today to get a clean install after many unneeded installs when I was first learning. I had been using the x64 version, because I have an AMD x64 processor. But today I installed the x86 version bcause I herd the x64 version had some short commings still (no idea how valid that is now after 8.10). The origional version I had instlled was 8.04 x64 and it worked fine on my laptop, but I am having major problems with my graphics card/drivers (nvidia 6150). 
First I couldn't get my graphics drivers to install at all, but I found something called evin that fixed it. Then I restarted and it told me that I should shitch to version 177 so I did. My card is online now, but I keep getting flickers, and some of the windows are not displaying correctly when not the active window, (taskbar blanking out, windows going blank and showing the objects behind them).
I was wondering if switching back to the x64 version might fix this (to my understanding I have a processor/RAM intergrated graphics card), but I know I had none of these problems with the x64 version.
If you have a sugestion on how to fix this, or and reason why the x64 worked but the x86 doesn't, I can use some help solving this.

---

### Post by taseedorf on 2009-01-12
problem is easily fixed.   install nvidia drivers manually.

download them at the nvidia website

than disable the drivers you're using now ( you DONT want to be using restricted drivers)

than quit out of gdm (if you're using gnome)

sudo /etc/init.d/gdm stop

than run the file you downloaded for the drivers.

---

