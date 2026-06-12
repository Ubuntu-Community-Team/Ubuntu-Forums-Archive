---
title: "How to install Ubuntu with pendrive on a HP mini?"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by honeybear on 2010-08-17
Hello,

I just bought a PC and would like to install LINUX Ubuntu on it. I never used ubuntu or linux before. Could someone help me how to install Ubuntu on this computer. The problem is that there is no cdrom and I never used linux before. I found only cdrom on the ubuntu website to be downloaded, or there is too dvd but I have not reader for any because it is a thin pc. as the picture shows below 

[http://www.engadget.com/2008/12/23/video-hp-compaq-mini-700-unboxed/](http://www.engadget.com/2008/12/23/video-hp-compaq-mini-700-unboxed/)

---

### Post by TriBlox6432 on 2010-08-17
Download the ISO.  Download and install unetbootin.  Run unetbootin.  Plug in your USB (select it from a list), select the downloaded ISO from a list (Something along the lines of: ubuntu_10_04_Lucid_Lynx.iso).  And the instructions from there are pretty straight forward.

Then you plug your USB in, restart the computer, enter BIOS (by pressing Esc, ff2, f10, or f12 at startup) and change the boot order to boot from USB.  Then exit with saving changes, and you will boot into Ubuntu, which you can install from there.

My recommendation:  Since you've never used linux, when given the opportunity, give Ubuntu and Windows equal space on your hard drive.  Just in case you don't like Ubuntu and want to go back to Windows.

---

### Post by jonnywombat on 2010-08-17
there is a how to [here]("https://help.ubuntu.com/community/Installation/FromUSBStick")

HTH

---

### Post by oldfred on 2010-08-17
Some more info on a similar install:

Ubuntu Netbook Install ASUS EeePC with startup creator to make USB install
[http://members.iinet.net/~herman546/p28.html](http://members.iinet.net/~herman546/p28.html)

---

### Post by honeybear on 2010-08-19
Hi !

I have finally managed to installed the PC !! wow 
- well

little problem, I get a GRUB 17 at boot. The ending of the installation during grub-install got me an alert that the grub couldnt be installed successfully. What to do now?

---

### Post by oldfred on 2010-08-19
Can you boot the USB as the liveCD to run Ubuntu?

If so run this. Also what are the specs on this computer does it meet the mimimums for install?

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
[https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight%20GUI%20alternative%20%28Xubuntu%29](https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight%20GUI%20alternative%20%28Xubuntu%29)

---

