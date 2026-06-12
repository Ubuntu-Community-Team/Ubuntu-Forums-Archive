---
title: "weird boot into HD with XP from HD with Ubuntu"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by s1baker on 2010-12-22
hi,
I have Ubuntu 10.10 32 bit installed
--------------------------------------
Here is the setup I have:
 I have a HD with Ubuntu on it and I also have another HD with Windows XP on it ( my old, original XP ). Both are hooked up together on the ribbon in the box and I switch the boot either into Ubuntu or XP through the bios by setting the bios as to which HD I want to boot off of. I have been doing this for a month now, almost daily.

 On the Ubuntu HD, I have VirtualBox installed with Windows XP on it. I am using this setup as I transition away from my old XP HD to my Ubuntu HD.

 Here is what happened:
I rebooted Ubuntu ( exactly like I always do to reboot back into my HD with my old XP on it ) and the Windows XP that is installed in VirtualBox on Ubuntu booted up instead. Of course, VirtualBox was not running or anything, this was a clean boot after the bios was correctly set to boot off the HD with my original (old) Windows XP on it. Strange.

 I rebooted ( and I checked to make sure that the bios was correctly set for the old HD with XP on it to boot, which it was ) and tried again and this time the (old) XP did boot.  

 I am thinking that the boot loader that my (old) XP uses, for some reason, incorrectly tried to boot the Ubuntu/VirtualBox XP, but that seems strange. I can't afford to mess up my (old) XP HD as I still use it for work.
 Any ideas?

---

### Post by cariboo on 2010-12-22
It is almost impossible to boot from the XP vm, as all it basically is, is a large file in your home directory, it doesn't do anything to the mbr.

---

### Post by s1baker on 2010-12-23
It is almost impossible to boot from the XP vm, as all it basically is, is a large file in your home directory, it doesn't do anything to the mbr.
__________________
Forum Do's & Don't's|Malicious Commands 

I am not booting from XP VM, I am rebooting from Ubuntu to another hard drive in my box that has Windows XP on it. These 2 hard drives are connected to the same box via a common ribbon, one connection of the ribbon to one HD, the other connection of the ribbon to the other HD. In the process of booting from my HD that has my Ubuntu on it, to the HD that has Windows XP on it, for some reason, the boot process tried to load the Windows XP that was on the Ubuntu HD in the VirtualBox. The question is why? 
.
That is my puzzlement and why I asked the original question

---

