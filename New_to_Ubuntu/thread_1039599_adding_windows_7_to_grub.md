---
title: "adding windows 7 to grub"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-01-14
i just did a fresh install of ubuntu 8.10 and decided while i was at it to try the windows 7 beta so i schrunk the ubuntu partition by 20gb and created a ntfs parttion which i installed windows 7 on.  i then went to restore grub but there is no entry for windows 7.   is there a way to add one?

---

### Post by SunnyRabbiera on 2009-01-14
there probably is, as XP and vista can be listed in grub so it makes sense.
Maybe the instructions to add vista to grub can apply...

---

### Post by 73ckn797 on 2009-01-14
> **mamamia88 said:**
> i just did a fresh install of ubuntu 8.10 and decided while i was at it to try the windows 7 beta so i schrunk the ubuntu partition by 20gb and created a ntfs parttion which i installed windows 7 on.  i then went to restore grub but there is no entry for windows 7.   is there a way to add one?

You could use "Super Grub Disk" and let it fix things.

You may possibly be able to add the following at the end of the grub menu:

```
# This entry automatically added by the Debian installer for a non-linux OS
title        Microsoft Windows 7 Beta
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```

Edit the "(hd0,0)" to whichever partition it is installed on.

I have not loaded 7 on this system but I do have XP. Windows 7 is on another computer but dual boots with XP. It ought to work.

You will need to open terminal and type:

```
gksudo gedit /boot/grub/menu.lst
```
Then enter password. This entry goes at the very last. You will also find a lot of useful info in the grub menu.lst.

---

### Post by mamamia88 on 2009-01-14
if i add that entry can it screw anything up if it doesnt work or will i just have useless text in menu.lst if it doesnt?

---

### Post by 73ckn797 on 2009-01-14
> **mamamia88 said:**
> if i add that entry can it screw anything up if it doesnt work or will i just have useless text in menu.lst if it doesnt?

It would be useless text. Always make a back-up of the menu.lst prior to editing.

If you paste it at the very end you should be good to go. The Ubuntu is probably the default OS.

Post your /boot/grub/menu.lst info. The last part that looks similar to this:
```
## ## End Default Options ##

title        Ubuntu 32bit 8.10, kernel 2.6.27-9-generic
root        (hd1,0)
uuid        33b41abc-de92-4925-aeb3-815844a1cf66
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=33b41abc-de92-4925-aeb3-815844a1cf66 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 32bit 8.10, kernel 2.6.27-9-generic (recovery mode)
root        (hd1,0)
uuid        33b41abc-de92-4925-aeb3-815844a1cf66
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=33b41abc-de92-4925-aeb3-815844a1cf66 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 32bit 8.10, memtest86+
root        (hd1,0)
uuid        33b41abc-de92-4925-aeb3-815844a1cf66
kernel        /boot/memtest86+.bin
quiet

```If nothing else is below this section then just paste in or add/type the info I gave you, with necessary edit to the drive/partition info applicable to your system.

You could let someone here make the changes so you can just paste into the grub menu.

---

### Post by chriscross93 on 2009-01-14
I've used this tutorial many times - for xp, vista, and 2000.  The windows version dosen't matter (idk about win 7 though).

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm")

---

### Post by kansasnoob on 2009-01-14
I think you should be able to follow this basic guide:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

I think you could name the new win "OS puppy-poop" and it should still boot, as long as you have the rest right:

> title Puppy Poop
root (hdx,y)
makeactive
chainloader +1 

Of course the x and y in "root (hdx,y)" must be indicative of the proper drive and partition!

---

### Post by mamamia88 on 2009-01-14
so if ubuntu is installed on my main partition and windows 7 is installed on partition sda2 does that mean the partition is (0,2)?

---

### Post by mamamia88 on 2009-01-14
thanks everybody it worked

---

### Post by 73ckn797 on 2009-01-14
> **mamamia88 said:**
> so if ubuntu is installed on my main partition and windows 7 is installed on partition sda2 does that mean the partition is (0,2)?

YEP, but you found that out already.

---

### Post by Patricrawley on 2009-01-14
Try this: [http://ubuntuforums.org/showthread.php?t=1036632](http://ubuntuforums.org/showthread.php?t=1036632)

---

