---
title: "do I need 3 kernels on GRUB?"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by DarkestStar on 2010-03-09
Have I 3 kernels on GRUB?

[B]Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic[/B]
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda2
Found Windows Vista (loader) on /dev/sda3

Do I need 3 or can they be tidied up and have just 1?
Only installed 9.10 once and ran from a live cd a few times

---

### Post by MichealH on 2010-03-09
I agree they can be in the way but you may need a older version one day so I would keep them there If you would just like 2 then just tell me and I will give you the remedy.

---

### Post by MelDJ on 2010-03-09
its better to have them in case one fails

---

### Post by bcbc on 2010-03-09
You can remove the ones you don't want - I keep at least two just in case.

Just go into Synaptic - it's easiest to search on the version (e.g. 2.6.31-14) and then you'll see three items you can mark for complete removal. There's a hook that will automatically run update-grub for you and they'll be gone from the menu.

If it's just the menu that bothers you it's possible to create a custom menu that always boots the latest kernel. Or gives you a choice between the latest kernel and windows - without all the other clutter: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

---

### Post by Terry of Astoria on 2010-03-09
The kernels are listed because they were from upgrades. The purpose is so that if your computer becomes unstable due to a kernel upgrade, you can roll back to a previous one.
One way to control the grub menu items is by using the GUI program startup-manager. Grub2 I think you will have on your 9.10 installation and it's a bit different from the way grub has always been, but I'm sure there's a good way to edit the entries. I used to edit my /boot/grub/menu.lst to remove those extra entries, but I think it's done differently now. I don't know what you're supposed to do now if you wanna do it by hand, but I have tried startup-manager and it works OK. I think you can
```
sudo apt-get install startup-manager
```
And then you will find it under your administration menu.
It's advisable to keep the previous kernel entry until you are sure that the new kernel works fine.

---

### Post by USB_NL on 2010-03-09
I also have new kernels. I got them after updating.

The old ones are there so you can switch back if your systems dosn't work properly, i guess. 

How to remove old kernels from the grubmenu I havent googled or done it. 
So I cant help you now.

---

### Post by MichealH on 2010-03-09
> **USB_NL said:**
> I also have new kernels. I got them after updating.

The old ones are there so you can switch back if your systems dosn't work properly, i guess. 

How to remove old kernels from the grubmenu I havent googled or done it. 
So I cant help you now.

I think a grub.cfg comes to mind!

---

### Post by DarkestStar on 2010-03-09
Found a thread that suggested ubuntu-tweak I will have a look at that and keep the latest (19,20) kernels
Thanks for looking

---

