---
title: "Two hard drive one for ubuntu 9.10 the other for xp"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by soltero5965 on 2009-12-21
Hello I installed Ubuntu 9.10 on my 80 g hd and i plan to install windows xp on my other 40 g hd on the same computer, will it work?
        I used to have xp first installed then Ubuntu next in one 80 g hd partitioned equally for both of the two OS on my other desktop no problem at all..but i'm not sure about installing ubuntu first then xp...anybody..thanks

---

### Post by NoaHall on 2009-12-21
Remove the Ubuntu HD first, then install windows. Then boot into ubuntu, and run the command ```
sudo update-grub
```

You may have to play around with menu.lst

---

### Post by ScottinSoCal on 2009-12-21
Microsoft doesn't play well with others. If you install XP last, it'll trash your boot and your system won't recognize the Ubuntu any more. It can be fixed, but if you're asking this question, I'm going to go out on a limb and guess that you wouldn't know how to fix it, which would be frustrating.

---

### Post by llawwehttam on 2009-12-21
If you do have a problem with your bootloader afterwards its time for SuperGRUB!!!!

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by oldfred on 2009-12-21
If it is 9.10 new install you will have grub2. There will be no menu.lst and supergrub has not yet been updated to work with grub2. Do not mix grubs or there are real problems.

The new grub2 is very good at finding other operating systems. Just make sure when you install windows that drive is set to boot first so windows installs its boot loader to that MBR. Then switch back and run the update-grub to find windows.

If they are Sata drives your BIOS usually lets you switch boot order. If older pata drives you have to do the master/slave settings either cable select or jumpers.

---

