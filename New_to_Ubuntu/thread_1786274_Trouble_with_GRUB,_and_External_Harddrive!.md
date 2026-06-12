---
title: "Trouble with GRUB, and External Harddrive!"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by tehl33tjim on 2011-06-19
Okay, my situation seems to be fairly unique in that I can not find help for this anywhere.  This is what happened;

I had Ubuntu 10.04 installed on my laptop.  That laptop's motherboard eventually burned out, so I bought a USB external enclosure for the harddrive.  Now I connected it to my mother's laptop (with Windows7 on it), and booted - which led me to somehow installing GRUB on my mother's laptop.  HOWEVER - if I don't have the external harddrive connected, I get an error:
```
error: no such device: a51d5241-e874-46a1-99b5-2fb9f8520279.
grub rescue>
```

Now the problem: the external harddrive was ripped from the USB socket while I was using Ubuntu, causing it to freeze, and me having to reboot the laptop.  Now whenever I choose Ubuntu on the grub menu, it hangs at a black screen (I'm assuming some data was totally messed up when it was unplugged during use).

Now my mother's Windows 7 went to be reinstalled, but when it "loads up for the first time" it gives an error saying that it can not finish.  Which I am assuming has to do with grub.


I tried using the SuperGrubDisk via Unetbootin - but I have no clue as to what exactly to choose [most options give back an error].  I can't go into Ubuntu at all, and I can't go into Windows at all.  I tried using Unetbootin with the Ubuntu install on it, to go into LiveCD mode - but that also does not work [gives me errors].

Can anybody give me any sort of help?  I would greatly appreciate it.

---

### Post by cariboo on 2011-06-20
If you can boot Windows 7, but can't get anything further than the initial setup, you have problems that have nothing to do with grub. A fresh install of Windows will overwrite the MBR removing grub. It sounds like, you may be looking at other problems.

Also if you have an Ubuntu install on an external drive, you don't have to make any changes to the computer, other than setting it to boot from USB.

---

### Post by tehl33tjim on 2011-06-20
None of the installs were working at all - so I went ahead and wiped the harddrive (which seemed to be the only way for me to remove GRUB).  Now the Windows 7 install works - which leads me to believe GRUB was indeed the culprit.

Ubuntu was capable of running in Live mode also - (for testing purposes).  So this is all well and good now.

[solved] :D

---

### Post by oldfred on 2011-06-21
All you had to do was reinstall the windows boot loader to the MBR of the internal drive and install grub2's boot loader to the external drive. I think I have posted those instructions at least a 1000 times.:)

For reference one of many links:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

