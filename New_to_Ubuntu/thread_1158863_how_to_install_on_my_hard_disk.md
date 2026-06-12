---
title: "how to install on my hard disk"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by Rajiv Dharmadhikari on 2009-05-14
Dear Sir,
I am new to Linux and no nothing about it, my system has three drives partitioned as C:, E: and F:
Windows is in C: and E: is having space of about 50 gb and some photos of my family.
I want to install Ubuntu on my E: drive from where it can boot itself or windows.
I do not want to save it to CD as I do not know how to do it.
Please anyone can help. I can download it from internet. I do not want to buy or use a CD. Please advise if it can be possible for me choose which operating system to boot and how ? I searched on internet for past4 hours but do not know how to install it directly to hard drive without involving CD.

---

### Post by Elfy on 2009-05-14
[https://help.ubuntu.com/community/Installation#Installation](https://help.ubuntu.com/community/Installation#Installation) without a CD

---

### Post by Rajiv Dharmadhikari on 2009-05-14
well i am not able to follow

---

### Post by ainsworth_t on 2009-05-14
Check out Wubi, the Ubuntu Installer for Windows ([http://wubi-installer.org/](http://wubi-installer.org/)). It's officially supported by Ubuntu, you can install Ubuntu through Windows without having to use a CD, you can select what drive you want to install it on, it installs within an existing filesystem so you don't have to worry about partitioning and formatting (and possibly losing data), and it creates a dual boot environment so you can boot into either Windows or Ubuntu. If you end up not liking Ubuntu, you can uninstall it from within Windows. Good luck!

---

### Post by Rajiv Dharmadhikari on 2009-05-14
Thank You Sir, but now I have already started downloading the ubunto*.iso file .  I would try to see if I can copy it to a CD. If I am not able to do that then I would run wubi.exe and download all files again.

---

### Post by lisati on 2009-05-14
> **Rajiv Dharmadhikari said:**
> Thank You Sir, but now I have already started downloading the ubunto*.iso file .  I would try to see if I can copy it to a CD. If I am not able to do that then I would run wubi.exe and download all files again.

If you download a copy of [wubi]("http://wubi-installer.org/") and put it in the same directory as the ISO file, you can run Wubi without putting it on a CD

---

### Post by Rajiv Dharmadhikari on 2009-05-14
Actually I may have to delete windows from my system and therefore I am not too sure that in that case also if I use wubi then also ubuntu will be able to boot or run

---

### Post by lisati on 2009-05-14
Wubi needs to have Windows on your system to be able to work.
If you need to delete windows for some reason (not recommended while you are finding your way around Ubuntu), and if making a CD is a problem, then there are other options, like using a USB memory stick.

---

### Post by ad_267 on 2009-05-14
If you have a CD that is the easiest way. Just make sure you select the option to burn an image to cd.

See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) for instructions on burning the image to a CD. That shows you how to use Infra Recorder, but you should be able to do the same thing with any disc burning application.

---

### Post by halitech on 2009-05-14
WUBI requires windows to run. What do you mean by you may have delete windows?

---

