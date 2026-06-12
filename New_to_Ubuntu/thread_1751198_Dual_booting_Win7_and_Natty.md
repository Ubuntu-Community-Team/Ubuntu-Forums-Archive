---
title: "Dual booting Win7 and Natty"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by iBurley on 2011-05-06
Alright guys, so I'm not a complete noob when it comes to Linux, I've even run Arch and played with it in a Virtual machine, got gnome on it and all. But I have some crazy issues whenever I try to dual boot Ubuntu with Win7, so before I tried it again with the new release, I thought I'd post and see if anybody has fixes for them.
 
One of my biggest issues is that if I screw something up (becuase I am a complete noob to Wine, and usuallymess it up) and need to re-install Ubuntu, it wipes out my Win7 installation and I lose everything and need to restore from my external hard drive. Other than this, most of my issues are cosmetic. I have a huge issue with Grub. It looks nasty, and I can't seem to change the order in which it chooses an OS. When I turn my computer on, I would like it to automatically boot into Win7 unless I'm holding some sort of button. If you have ever run Ubuntu from an external hard drive, you know what I'm looking for. I basically would like to be able to go into a boot meny (like Grub) if I wantto, but not have to see it otherwise. Is there any way to do this?
 
Thanks, and yes, I know, I'm far too picky. lol

---

### Post by techunit on 2011-05-06
For you I think may just want to use Wubi. Just put the Ubuntu CD in your computer while Windows is running and click Wubi installer in the autorun prompt. 

If you must have a legitimate dualboot then you should do plenty of research on the subject. Read over this wiki.
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")
You can get Ubuntu to be second in the boot menu however I am not sure how. If you want a nice looking Grub menu try Burg. **However this won't work with WUBI.**

---

### Post by CyberNerdz on 2011-05-06
Are you using [WUBI]("http://www.ubuntu.com/download/ubuntu/windows-installer") ?

I was able to install Ubuntu 11.04 in Windows 7-64 SP1 Ultimate successfully. After Windows Loader, it takes you to Grub wherein you can manually edit it if needed. The only hurdle was installing my Nvidia drivers and had to go to terminal and install it there manually. Then did the update/upgrade from there. After that, everything went smoothly.

---

### Post by YesWeCan on 2011-05-06
This should be pretty easy to set up.
Are you dual booting off the same HD or off separate HDs?

I would recommend adding Ubuntu to your Windows bootloader rather than adding Windows to Grub. You may find it easier to configure this way. This also means if you delete Ubuntu you will still be able to boot Windows. You can do this using free, EasyBCD; a Windows download.

If you install Ubuntu on the same HD tell it to put Grub in the same partition as Ubuntu, not in the MBR.

If you install Ubuntu on a separate HD, disconnect your Windows disk while you do it. This will make sure Grub is put on the MBR of the Ubuntu disk rather than overwriting your Windows MBR. Then reconnect the Windows disk. Then you can do the Easy BCD thing.

If you want to add Windows to Grub's menu do "sudo update-grub". To configure Grub to set the boot order and timeouts and all you need to manually edit the /etc/default/grub file and then do an update-grub.

---

### Post by iBurley on 2011-05-07
I am not using Wubi, and I will be installing them on the same hard drive. I just don't know how one goes about using the Windows boot loader instead of Grub.

---

### Post by nomekop on 2011-05-07
use wubi, if you need to reinstall ubuntu all you do is boot into windows 7 and uninstall ubuntu and you can just download it again and windows will not be messed with

---

