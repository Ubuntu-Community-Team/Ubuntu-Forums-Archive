---
title: "Image breaking up badly on Video+DVD playing."
date: 2009-02-12
forum: New to Ubuntu
---

### Post by jono2009 on 2009-02-12
New PC, freshly installed Ubuntu8.10, have my driver and all updates. 

Playing video clips that I have on my PC and movies using my CD-RW/DVD, the image pulsate and breaks up badly.  

Also I keep reading about make sure you have "resricted, multiverse, universe, etc". I gone to Synaptic Package Manager, but I wouldn't know were to start.

Thank you for your help.:popcorn:

---

### Post by RomeReactor on 2009-02-12
Hi. What video card do you have? Is the video a DVD, or in HD (720p or higher)? Do you have Desktop Effects (Compiz) running)? If so, try disabling them in 'System->Preferences->Appearance->Visual Effects' and see if that makes a difference. Also, please post more details about your system--CPU, RAM, etc.

---

### Post by jono2009 on 2009-02-12
> **RomeReactor said:**
> Hi. What video card do you have? Is the video a DVD, or in HD (720p or higher)? Do you have Desktop Effects (Compiz) running)? If so, try disabling them in 'System->Preferences->Appearance->Visual Effects' and see if that makes a difference. Also, please post more details about your system--CPU, RAM, etc.

RomeReactor thanks for helping,

I disabled Desktop Effects and that has fix the problem.  

Installed ATI/AMD propriety FGLRX graphics driver
by Ubuntu.

Here is my System Details. 
Performance Asus/Gigabyte Motherboard
AMD Triple Core 8450 CPU 2.1GHz
4GB 800MHz DDR2 Ram
500Gb 7200RPM Serial ATA 2 Hard Drive
160Gb 7200RPM Serial ATA 2 Hard Drive
512Mb ATI Radeon 3870 PCI Express Video Card With DVI, HDMI
Integrated High Definition Audio
Integrated 10/100 Network Adapter
20 x Dual-Layer Serial ATA DVD Burner
450W Power Supply

I have yet to get try and use Compiz, I would prefer not to disable Desktop Effects each time I watch a movie or video clip. Still a newby at Ubuntu, but not going back to M/Soft.

---

### Post by RomeReactor on 2009-02-13
I'm not familiar with ATI cards (still waiting for my first one to arrive), so I'm afraid I can't be of much help there; however, by the specs you posted the system is certainly powerful enough to easily run HD video. It's possible the problem lies in the configuration of the driver (or a bug in it), or maybe wrong BIOS settings. Hopefully someone with actual experience with ATI cards can be of assistance to you.

---

### Post by petronell on 2009-02-13
i use vlc for watching video.

you can enable desktop effects and then in vlc go to tools menu and choose preferences.

under video change output to x11 video output. it works for me.

daveR

---

### Post by jono2009 on 2009-02-14
RomeReactor, petronell thank you both for helping me. 
As a complete noob, I was unable to find this post untill now 14 hours later,(search under my own name), I'm sorry for taken so long. 

RomeReactor, yes the answer is in the wrong BIOS settings I'm sure, I'm carefully spending more time in there.
 
petronell, I done as you suggested to VLC and problem Solved.

One happy noob
jono:popcorn:

---

