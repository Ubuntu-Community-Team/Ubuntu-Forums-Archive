---
title: "GeForce 9500 M GS driver"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by pbsilva on 2010-09-08
Hello guys,

I have been using Ubuntu 10.04 LTS Lucid Lynx for quite a while now. I fully migrated from Windows. Everything is working pretty well and it's running smoothly. I have been able to solve all the small problems I faced with help of google and linux-geek friends, there's just one problem I couldn't solve yet and that's why I am asking here for help. I have an Acer Aspire 5920 G with a NVIDIA GeForce 9500M GS TurboCache Graphic Card and I would like to know whether there are operating drivers for it. I tried to install both versions (173 and current) from the Hardware Controllers menu but those don't work as supposed. Thanks in advance,

pbsilva

---

### Post by Ctrl-Alt-F1 on 2010-09-08
I have a 9800M GS and the current drivers work fantastic for me.  I'm sure the driver would cover your chipset too.

What kind of problems are you having?

---

### Post by pbsilva on 2010-09-09
After I automatically installed the drivers with help from the System Menu as mentioned, the resolution during system boot is bad and then after logging in I experience all types of random shades, blinkings and distorcions in the screen.

---

### Post by YfoMp5QBh2 on 2010-09-09
I had a similar problem after using the ubuntu installer, but instead of booting to GUI it went straight to command line. My problem was resolved by re-installing the drivers from the Nvidia website and blacklisting noveau.
 
I'm still a noob myself but perhaps reading my thread might give you some ideas to solve your own [http://ubuntuforums.org/showthread.php?t=1565176](http://ubuntuforums.org/showthread.php?t=1565176) :)

---

### Post by pbsilva on 2010-09-29
I would like to share with those users facing a similar problem, that after quite some googling I found a "solution". The flickering noticed happens because of the adaptative settings of the GPU in the Nvidia X Server Settings. So if you turn this option to "performance", therefore disabling the GPU scaling, the flickering will be gone and everything will work kind of out of the box (at least for me it does). Just a note: As you have probably noticed the Ubuntu Logo during boot and shutdown gets a little bit disconfigured after the driver installation. Here's a solution for that: [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

