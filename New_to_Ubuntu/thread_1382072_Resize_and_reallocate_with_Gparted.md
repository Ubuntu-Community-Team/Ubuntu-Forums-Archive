---
title: "Resize and reallocate with Gparted"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by obonob on 2010-01-15
Hi, 

I've been using Ubuntu for a few weeks now and I can't figure this one out. I dual boot XP and Ubuntu. For reasons too long to explain, I needed to shrink Ubuntu's partition to reallocate the free space to the XP one. I ran Gparted from the Live CD (Mint since Gparted was not on my Ubuntu CD) but even then, I cannot unmount the extended partition. As I understand it, even if the ext4 can be played with (no key icon beside, unlike when you run it without the Live CD), the swap is still in use causing the whole partition to be locked.

Nevertheless, I shrunk the ext4 and it worked. The problem is that I cannot reallocate the free space gained to my ntfs partition since it is still contained in the dev/sda2. I can format it though. But not to ntfs (only ext and fat).

Sorry if all of this ain't clear : n00b and English is not my first language.

Thanks in advance !

---

### Post by drs305 on 2010-01-15
Please run this command and post the results. A screenshot of gparted with your current situation would be even better!
```
sudo fdisk -l

```

---

### Post by obonob on 2010-01-15
Oh ! That was fast ! :-)

Sorry, I should have thought of posting it in the first place. Here it is. I just noticed that I can format the unallocated space only when I boot normally but the option is not available when booting from the Live CD.[U]
[IMG]http://img686.imageshack.us/img686/8079/screenshotpj.png[/IMG]

[IMG]http://img686.imageshack.us/img686/5849/screenshot1pe.png[/IMG]
[/U]

---

### Post by audiomick on 2010-01-15
the unallocated space is inside the extended partition. You got it by shrinking sda5. You want to add the space to sda1.

To unlock the extended, you probably have to unmount the swap. I am not too sure, as I have not had exactly that situation. So click (right click?) on the keys next to swap and unmount it.

Then you need to shrink the extended down as much as it will go and apply, then you will be able to expand sda1

---

### Post by Cheesemill on 2010-01-15
Right click on your swap and select swapoff to unmount it, then resize sda2 then sda1.

PS - Gparted is called 'Partition Editor' on the menu in earlier versions of Ubuntu.

---

### Post by atomizer on 2010-01-15
you can do ```
swapoff
``` in a terminal to unmount your swap

edit: the above post says how to do it the graphical way (I'm a bit slow I guess)

---

### Post by obonob on 2010-01-15
Ok, I didn't see this option the first time. :oops:

In Gparted : "Could not deactivate
                    Killed"

Still locked.

Terminal : Killed

Then with fdisk -l, it still shows up so I don't know exactly what it means.

Could it be because I don't have much RAM (only 256) so it necessarily uses the swap ?

---

### Post by Cheesemill on 2010-01-15
Most probably.

Try using the [Gparted Live CD]("http://sourceforge.net/projects/gparted/files/"), it's alot lighter on resources than a Mint/Ubuntu CD.

---

### Post by obonob on 2010-01-15
Ok then, I'll try it tomorrow since I don't have any cd at hand. Thanks!

---

### Post by obonob on 2010-01-22
Sorry for the late response : a bunch of stuff got in the way.

I finally got a chance to try the GParted Live CD and it worked like a charm. So light I didn't have to execute the swapoff since it wasn't even using the swap in the first place.

Thanks a lot for your help and suggestions !

---

