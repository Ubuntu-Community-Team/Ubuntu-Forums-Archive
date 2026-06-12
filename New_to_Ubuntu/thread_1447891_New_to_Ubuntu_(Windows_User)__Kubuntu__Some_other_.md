---
title: "New to Ubuntu (Windows User) / Kubuntu? / Some other issues"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by w_tanoto on 2010-04-05
Hi! First let me introduce myself. I am a Windows user thinking of using alternative OS, and I have made a decision to use Ubuntu as secondary OS. I have installed Ubuntu in separate partition in someone else's laptop. I have also installed Ubuntu as Virtual Machine in my own laptop, but thinking to take the full advantage of my computer hardware and install it for real in separate partition.

I have my eyes set on Ubuntu. I tried Kubuntu, and I somewhat prefer Ubuntu. While I have made decision to install Ubuntu in dual-boot configuration with Windows 7 (I haven't installed it properly, still using that terrible Vista as main OS), I just want to be sure I made a correct decision. What is the exact different in functionality and theme between Kubuntu and Ubuntu (I can't be bothered with technical details, but I know Kubuntu use KDE, while Ubuntu use GNOME). If there is no real difference, then I'd probably stick with Ubuntu.

Also, does Linux has antivirus, or is it already secure as it is without anything? (Sorry for noob question, but I have no idea). If there is an antivirus, could you recommend me the free one?

Also, I am having some other issues, but I will post it later in the appropriate places since it will not be an absolute beginner stuffs. It's more like an issue related to Windows and its dual-boot, and what happened when I upgraded to Lucid Lynx

Thank you in advance.
w_tanoto

---

### Post by slooow on 2010-04-06
Difference between Kubuntu and Ubuntu: short answer is probably no real difference.

Antivirus for Linux: Clamav is focused on Windows viruses mainly for mail servers with windows hosts (probably not for you), chkrootkit is a utility to scan for rootkits and trojans. You need to read the manual and configure it correctly and then read the logfiles. But the main precautions is backup your data and reinstall if your system is acting weird.

Do you really want to upgrade to the latest version which will probably have a few instabilities and trouble your experience with Ubuntu. Why not settle for something more stable like Jaunty Jackalope 9.10?

Good luck.

---

### Post by mcoleman44 on 2010-04-06
You shouldnt need anti-virus. There are currently no known linux viruses.

---

### Post by arashiko28 on 2010-04-06
The differences between ubuntu and Kubuntu is the resources. KDE requires more resources than GNOME, if your computer it's up to it, (If has vista or w7, it is) then it's all up to the users preferences.

Also, welcome to the community, feel free to ask anything, we all started that way and still have to ask.

About antivirus, you won't need anything, windows virus can't run on Linux, because .exe extensions aren't used. In case you need one for windows, avast and clamav are good options. And there are no known virus for linux active on the moment. Also, check the sticky note about dangerous commands, on the absolute beginners area.

---

### Post by Nisal on 2010-04-06
> **mcoleman44 said:**
> You shouldnt need anti-virus. There are currently no known linux viruses.

if he going to dual boot it better if he have AV installed

---

### Post by w_tanoto on 2010-04-06
thank you all for the responses. I am planning to install Karmic Koala along with Windows 7 in a few days time (I just need some time to update my install files), but am worried about the boot manager when I upgraded to lucid lynx when it is released. As for antivirus, I will have norton 360 installed in Windows, but as everyone says, no need of antivirus, so I will not install any for my ubuntu.

Seems that I better continue in this thread about the booting issues: I don't want to use GRUB or GRUB2 as my "main" boot manager. I prefer to use Windows' boot manager which then calls GRUB2. My experience with GRUB2 is somewhat a disaster. I was trying to make Windows 7 default on someone else's laptop. It did work (after several hours trying that sudo things), but some entries appeared twice - GRUB2 tutorial was complicated and rare the time I tried to install it (and probably is still now). So, I am planning to use EasyBCD 2.0 beta to create linux entry. But the question is, will it work? If it does work, when I upgrade it to the stable release of Lucid Lynx, will GRUB2 be re-instated as the default boot menu again?

The thing is that I can't delay my Windows 7 installation as I have actually delayed installing it since October 2009. If I delayed it, some of the programmes I use will release an updated version, and I will have to update my install files again, which takes more of my time. I am pretty much set to install both now.

I am planning to install Ubuntu first, then Windows 7, then use EasyBCD to resurrect Linux. I am still curious though if that is going to work.

---

### Post by w_tanoto on 2010-04-06
> **arashiko28 said:**
> The differences between ubuntu and Kubuntu is the resources. KDE requires more resources than GNOME, if your computer it's up to it, (If has vista or w7, it is) then it's all up to the users preferences.

I will settle with GNOME. less resources, the better, though my laptop is a high-end.

---

