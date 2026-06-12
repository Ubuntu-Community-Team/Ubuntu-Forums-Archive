---
title: "Reading my Windows data on drive Ubuntu installed to"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Lord Stig on 2009-02-06
Hi.
I've just installed Ubuntu 8.10 (and fantastic it is, too!) on my external NTFS-formatted hard drive (in Windows terminology this appears as drive E). When I go back into XP (which is installed on my internal FAT 32 hard drive 'C') my external drive appears as normal and I can see that from Windows' point of view Ubuntu is installed in a folder on that drive (e.g. E:/Ubuntu/). In other words, Ubuntu is treated as any other folder. I did no partitioning at all and allowed Ubuntu to install itself through Windows off a live cd.

But I need to be able to see the other folders on my E drive!!!! However, when I boot Ubuntu the only icon I get for my "e" drive is "File System". Looking at this from a Windows perspective (the only experience I really have) there should be away to effectively 'go back' one folder from the file system folder and see all the folders I know I still have (I can get to them in Windows). I did look at partitions to see if that'd make it reappear but of course it's all on the one partition. Isn't it? (:-O

I've tried adding NTFS write support in the hope that I'll be able to do this soon and in the vain attempt that it might shed some light on this.

Apologies if I have picked the wrong area to post such a query and thanks for any advice in advance.

---

### Post by avtolle on 2009-02-06
You have installed through Wubi, from your description. I say this to be clear about your method of installation.

Have you tried opening "File System" to see what appears?

---

### Post by HermanAB on 2009-02-06
Nop, if you install Ubuntu that way, then you cannot access the top level file system.

Cheers,

Herman

---

### Post by Lord Stig on 2009-02-07
Thanks. I just installed it on my C drive instead.
One niggle - my PC has a built in speaker. All audio and video plays through the speaker but I don't want it to! It outputs to my amp (as I intended it to) as well so would be handy to stop the output to the internal PC speaker if possible. I've looked at various settings under the desktop's System menu but no luck so far.

---

### Post by HermanAB on 2009-02-07
Linux has various audio mixers.  Some have only a few functions, others seem to but has hidden features that can be enabled in a menu.  You need a mixer with more functions to get to all the features of your system.  You should already have aumix.  Try 'man aumix' for details, then play with *all* the settings.

Cheers,

Herman.

---

### Post by eriqjaffe on 2009-02-07
For what it's worth, a wubi install will mount the drive you installed Ubuntu on (E: in your first post, C: in your subsequent post) at /host, and it will mount any other hard drives you may have under /media.

So, to get to your "C:\Program Files" within wubi, it would be "/host/Program Files".  Just be careful not to mess with anything inside "/host/Ubuntu", as that can **really** confuse your Ubuntu install.

---

### Post by Lord Stig on 2009-02-08
Solved! Thanks for your help!

---

### Post by Lord Stig on 2009-02-08
Thanks. I may need that if I install Ubuntu on another PC.

---

