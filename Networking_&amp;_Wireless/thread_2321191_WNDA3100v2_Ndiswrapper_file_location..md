---
title: "WNDA3100v2 Ndiswrapper file location."
date: 2016-04-21
forum: Networking &amp; Wireless
---

### Post by clifton3 on 2016-04-21
First of all hi, I'm a first time poster.
Ok, every 2 or 3 years I torture myself by trying to get Linux to run on my computer. It's been two years and it's time to torture myself again.
I first tried the newest SUSE Distro, Leap 42.1. After two weeks of torture, I was able to get my Netgear WNDA3100v2 USB dongle to connect to the Wi-fi router.
I ended up using, ndiswrapper-kmp-default-1.59_k4.1.12_1-46.2.x86_64.rpm and ndiswrapper-1.59-46.2.x86_64.rpm. I felt pretty good about myself...until I found out that about every basic program I tried to install using 
Yast ended up not working. So I scrapped SUSE. I'm gonna try again using Ubuntu.
As I figured out, Ubuntu doesn't do rpm, but you already know that. 
The question is: where do I find the Ubuntu equivalent of the the 2 rpm packages I used in Suse to get the dongle to work?
I do not have internet access on Ubuntu until I get Ndiswrapper to work. Can somebody link me to, or tell me the proper names of the files I need? I've looked a bit, but I'm a bit confused
I will download them on work computer and then put them on a thumb drive and give it a go on Ubuntu.

Thank you for your time

---

### Post by Bucky Ball on 2016-04-21
Welcome. Have you tried installing the fresh 16.04 LTS and plugging it in? You'll probably need to install the daily build, but it is officially released today (21st of April, or supposed to be). Not sure if it's working in that yet but it is possible to get it working on some machines in previous versions of Ubuntu.

Have you done a search for 'Netgear WNDA3100 ubuntu'? There are a ton of threads on here and elsewhere dealing with it. It has been problematic, which is why I suggested the new 16.04 which will have drivers for newer hardware and hopefully that includes the ones for your wireless card.

ndiswrapper is also available in Ubuntu, but I would try everything you can to avoid and go for that as a last resort. A problematic kludge and mostly redundant now for the cards it was needed for (and has been for some time). There is, of course, the occasional exception. :|

---

### Post by clifton3 on 2016-04-21
Thanks for replying. 
Right now I'm trying 14.04.4 LTS.  When I look at the WNDA3100v2 threads, it's a lot of apt-get stuff (can't use it if I'm not networked) and examples of commands to find out if the Wi-Fi adapter is recognized. I'm up on that because I already installed it on Suse.
I just need to know the appropriate 2 files that work with Ubuntu. Like maybe the .deb version of the rpms that worked with Suse. If I find these, I'm pretty sure I can get it going.
16.04 LTS? All I see is the 14.04.4 LTS. Right now, I'd be happy just to get the Ndiswrapper working so I could at least use the internet to perhaps figure out how to do it properly.
Thank you.

---

### Post by clifton3 on 2016-04-21
Ah ok, now I see about 16.04. In the mean time I downloaded a few things and I'll see how it works.

---

### Post by Bucky Ball on 2016-04-21
Make your life a LOT easier if you could get online with a cable to work on wireless.

---

### Post by chili555 on 2016-04-21
Check here: [http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=trusty&section=all](http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=trusty&section=all)

You probably need -common, -utils and -dkms. The ndiswrapper-dkms package depends on dkms itself, so get that, too. Be sure to get, in the case of -utils, the 32- or 64-bit version, as appropriate. Get all the debs on to your desktop and then, in a terminal:```
cd ~/Desktop
sudo dpkg -i dkms*.deb
sudo dpkg -i ndis*.deb
```

---

