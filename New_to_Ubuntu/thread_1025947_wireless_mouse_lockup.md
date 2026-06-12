---
title: "wireless mouse lockup"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by _hyphen on 2008-12-30
<*EDIT - uninstalled ubuntu - no more having to choose between being able to use keyboard during OS selection or using mouse with Ubuntu...these are the sort of problems that need easy fixes before linux can win over standard user market effectively. Wireless keyboard/mouse combos running off a shared usb receiver are far too common to ignore in basic functionality*>


I have been gone from linux for a while, but I have just returned and installed 8.04 LTS off the mailed disc, and here is the situation

I have a wireless keyboard and mouse which share a usb receiver (micro innovations set). After about 5 minutes the mouse (just the mouse) will stop responding, only a reboot changes this.

I can eliminate this lockup problem by disabling legacy usb support in my bios - BUT then I can no longer use my keyboard at GRUB to select an OS...and I do not always want to boot into Ubuntu.

So either no keyboard at GRUB, or mouse-freeze in Ubuntu - neither one of these standing choices work for me of course :)

I have also tried the other suggestion I found on the boards here involving a nano editing of menu.lst using force irqpolling or somesuch, but that did not resolve it either.

What I find interesting - is the keyboard continues to work when the mouse dies and they are using the same receiver..

Any thoughts on this? The OS is pretty useless to me in this state, as I can't sacrifice my boot options nor work around rebooting every 5-10 minutes when I Am in linux

Thanks!

---

### Post by jimmy the saint on 2008-12-30
My mouse was locking up and stuttering as well.  This may or may not have anything to do with you problem, but when I replaced the battery it fixed it.

---

### Post by xjcannonx on 2008-12-30
Energizer also worked for me, hopefully this will work for you too

---

### Post by _hyphen on 2008-12-30
It isn't a battery issue, but thanks for looking. Everything works fine in windows, and in ubuntu when i disable legacy usb support in the bios. However, as I mentioned, that solution alone is not viable as it prevents the keyboard from working for GRUB.

---

