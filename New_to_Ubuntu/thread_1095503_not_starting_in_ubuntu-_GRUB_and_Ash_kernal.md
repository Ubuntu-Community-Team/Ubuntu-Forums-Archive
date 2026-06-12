---
title: "not starting in ubuntu- GRUB and Ash kernal"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by chemgrl08 on 2009-03-13
Here's the deal: I installed ubuntu about a year ago on this old computer I have (Dell, 1995-98) It worked then. Kind of left the computer alone a while, took out one of the two hard drives it had and tried to boot it up on ubuntu again. It seems like it starts to boot (I see the ubuntu logo with the loading bar) but then it never makes any progress on the bar, and I get a black screen that says "BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash) Enter 'help' for a list of built in commands.
(initramfs)  "
And it seems no mater what I put in nothing happens. If I type reboot, it will reboot but the same thing will happen. If I type "exit" it just repeats the above message. typing help shows me commands, but I am a n00b to linux and don't know what they mean.
Perhaps I disconnected something accidentally when removing the other hard drive? If I need to reinstall, I can just boot the computer with the appropriate CD (with ubuntu on it), right?
Thanks for any help you can offer.

UPDATE:
Tried to reinstall ubuntu by making a new CD (did all the checks and everything) but now that same screen comes up, with only slightly different numbers/words- "BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) Built-in shell (ash) Enter 'help' for a list of built-in commands.
(initramfs)  "
Grrr please help.

---

### Post by kellemes on 2009-03-14
You installed the latest Ubuntu 8.10?

---

### Post by presence1960 on 2009-03-14
I had the same problem on Mint5. I had to edit my menu.lst for Mint (not recovery mode or memtest) to this:
> # This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Linux Mint x64, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sdb1 ro splash all_generic_ide floppy=off irqpoll 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot

The kernel line is where the edit was made after "ro" in place of quiet splash. I don't know if this will work on Ubuntu but give it a shot. Mint is Ubuntu based.

---

