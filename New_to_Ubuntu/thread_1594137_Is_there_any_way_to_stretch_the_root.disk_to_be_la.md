---
title: "Is there any way to stretch the root.disk to be larger?"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by egervari on 2010-10-12
I just installed ubuntu to see if I liked it, and I do. I only allocated 10GB to it, and I'd like to increase it to 20 or 30 without having to redo everything I've already done. How can I do this?

---

### Post by gyussz on 2010-10-12
> **egervari said:**
> I just installed ubuntu to see if I liked it, and I do. I only allocated 10GB to it, and I'd like to increase it to 20 or 30 without having to redo everything I've already done. How can I do this?

You can do it with a Live CD with System -> Administration -> GParted. It can expand/shrink/move etc. your partitions. Before you do anything, make sure you know what you're doing. I also recommend a backup.

However If you have a Windows installation too, maybe it's better to format the Ubuntu partitions and do a fresh install, or make a backup disk with remastersys or clonezilla. You will surely avoid boot-related errors by installing a clean or a cloned, pre-configured system.

Hope I could help.

---

### Post by egervari on 2010-10-12
In GParted, it doesn't display the 10GB that I allocated to Ubuntu using the Windows Installer. It just tells me about my actual full hard disk partition (/dev/sda) that is mounted at /host.

I actually just want to resize the initial 10GB I allotted using the Windows installer.

---

### Post by gyussz on 2010-10-12
Do you see that partition with the Windows Installer? Have you tried running gparted as root? (Don't know what's wrong with it, but it should show your partitions.) Post a screenshot if you can, maybe that could explain more.

---

### Post by yetiman64 on 2010-10-12
> **gyussz said:**
> Do you see that partition with the Windows Installer? Have you tried running gparted as root? (Don't know what's wrong with it, but it should show your partitions.) Post a screenshot if you can, maybe that could explain more.

root.disk indicates a "wubi" install of Ubuntu and as such Ubuntu is a program / filesystem in Windows, fully contained within the NTFS filesystem. It won't show as a separate partition from within gparted like a typical "side by side" partition dual boot setup.

---

### Post by egervari on 2010-10-12
Well, I'm assuming it is as root because it asked me to put my password in.

It does show me 2 partitions - one for my external hard drive, and one for my only hard drive.

The windows installer used 10gb from my 700gb drive to dedicate towards ubuntu. I can see this fact when I check on my drive information (System->Adminstration->Drive Utility). But this fact is not present in GParted.

Should I boot back into windows and re-run the installer? Will it let me rescale the drive without destroying all of my configuration? There were several specific things I had to do to get ruby working correctly, java, etc. I'd rather not have to redo it.

---

### Post by egervari on 2010-10-12
> **yetiman64 said:**
> root.disk indicates a "wubi" install of Ubuntu and as such Ubuntu is a program / filesystem in Windows, fully contained within the NTFS filesystem. It won't show as a separate partition from within gparted like a typical "side by side" partition dual boot setup.

Yes, that's right. Can I use wubi to scale it again without destroying everything?

---

### Post by yetiman64 on 2010-10-12
> **egervari said:**
> Yes, that's right. Can I use wubi to scale it again without destroying everything?
Sorry, but I don't know enough about using wubi, (though I know fairly well as a dual-booter that it causes lots of headaches when wubi and "standard" dual booting are confused in these forums).

I would suggest you wait for someone with more wubi experience than myself to help you with that. Cheers and good luck. yetiman64

---

### Post by gyussz on 2010-10-12
[https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?](https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?) Try this

EDIT:
By the way, if you really like Ubuntu, give it a separated partition :) I think Wubi affects performance a bit.

---

