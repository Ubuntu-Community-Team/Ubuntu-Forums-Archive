---
title: "Help! GRUB does not boot either Windows XP or Ubuntu!"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by Matthew Spinks on 2009-04-15
Okay, I'm a newbie so bear with me here for a while
Here's the story so far:
I was able to successfully install a dual boot of Windows XP professional and Ubuntu for my Dell Laptop. I didn't like how grub listed like five OS Ubuntu, recovery mode, NTFS/2000,etc. so I decided to edit the grub menu.lst to clean it up a little bit. I put in some hash # marks to clean up the menu a little and now when the grub menu comes up I cannot boot to EITHER of my operating systems. Both of my operating systems appear in the grub menu as they should, but they don't boot correctly. Instead when I choose Ubuntu it boots a mem test of some sort and when I pick Windows XP Professional it starts a Synaptic Recovery mode sort of thing.
Here's what I do know:
I did save a backup file of the menu.lst
Before I edited the menu.lst I had two windows operating systems listed. One was the XP Professional, (which used to work when I chose it) and the other was listed as NTFS/2000/XP or something like that, when I chose this one it used to start the recovery mode thing that I mentioned earlier.
Now I have only two menu options: Ubuntu and Windows XP Professional. As I mentioned before Ubuntu starts a mem test and XP starts the recovery mode.

I do need to know what went wrong with the menu.lst, (I'll save that for a later post) but what I need right now is a way to get into Ubuntu. Is there a way to use a grub command or perhaps the grub shell (using the live cd) to fix the menu.lst?

Here's what I get when I type 'e' in the grub menu for Ubuntu:
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-23-386 root=UUID=a03a3ed4-a16e-45db-8dd3-7750b782d622 ro quiet splash
initrd /boot/initrd.img-2.6.24-23-386
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-23-386 root=UUID=a03a3ed4-a16e-45db-8dd3-7750b782d622 ro single
initrd /boot/initrd.img-2.6.24-23-386
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=a03a3ed4-a16e-45db-8dd3-7750b782d622 ro quiet splash
initrd /boot/initrd.img-2.6.24-23-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=a03a3ed4-a16e-45db-8dd3-7750b782d622 ro single
initrd /boot/initrd.img-2.6.24-23-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.15-23-386 root=UUID=a03a3ed4-a16e-45db-8dd3-7750b782d622 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-386
root (hd0,4)
kernel /boot/vmlinuz-2.6.15-23-386 root=UUID=a03a3ed4-a16e-45db-8dd3-7750b782d622 ro single
initrd /boot/initrd.img-2.6.15-23-386
root (hd0,4)
kernel /boot/memtest86+.bin
root

---

### Post by meierfra. on 2009-04-15
Press "c" at the grub menu to get to the Grub command line. Then type

root (hd0,4)

kernel /vmlinuz root=/dev/sda5  ro

initrd /initrd.img

boot

---

### Post by Matthew Spinks on 2009-04-16
Yes! it worked. THANK YOU very much for helping out a newbie.
Quick question though, how come it was sda5 and not something else? I've searched around lots of other forums before posting here but no one really said as to how to find what location to type. (I think most of the time it was sda3)

---

### Post by meierfra. on 2009-04-16
> Yes! it worked. 
Great.

> how come it was sda5 and not something else?
Grub starts counting at zero.  So from  "root (hd0,4)" one can conclude that Ubuntu is  the 5th partition.

---

### Post by Matthew Spinks on 2009-04-25
Thanks again. Apparently the problem was that I didn't have enough of those hash # marks in the grub menu.lst I only put them in front of the line that held the title instead of hashing the whole thing. Edited it and it works great now. (And yes I completely forgot to count from zero)

---

