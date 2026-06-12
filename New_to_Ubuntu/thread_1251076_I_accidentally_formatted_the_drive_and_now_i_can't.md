---
title: "I accidentally formatted the drive and now i can't boot anything."
date: 2009-08-27
forum: New to Ubuntu
---

### Post by z400100500 on 2009-08-27
I'm trying to get ubuntu to work and I had it for a day, then saw i only had 2 gigs of free space (should've been around 14), so i reformatted the drive it was on. The grub loader 1.5 now gives Error 17 and it won't do anything. Changing the boot order doesn't help, and I can get to XP to recover anything. Help!!! :(

---

### Post by NoaHall on 2009-08-27
You'll have to install Ubuntu again.

---

### Post by DFlame on 2009-08-27
> **z400100500 said:**
> I'm trying to get ubuntu to work and I had it for a day, then saw i only had 2 gigs of free space (should've been around 14), so i reformatted the drive it was on. The grub loader 1.5 now gives Error 17 and it won't do anything. Changing the boot order doesn't help, and I can get to XP to recover anything. Help!!! :(

Did you have both Windows and Ubuntu installed (a 'dualboot' system)? If so, it's possible to get into Windows XP if you want to do anything there.

If you'd still like to use Ubuntu, follow the suggestion above and re-install it from disc. This will restore the GRUB loader.

Post again with which way you'd like to go (Restore XP only or restore the dualboot) and I'm sure we can help more specifically.

---

### Post by Mark Phelps on 2009-08-27
> **z400100500 said:**
> ... and I can get to XP to recover anything. Help!!! :(

I'm guessing this is a typo and what you mean to say is that you can't get to XP.  In that case, you may have wiped out XP when you formatted the drive.

One way to check is to boot from the LiveCD, open a terminal, and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  If XP is still there, it will show the XP partition(s).

---

### Post by z400100500 on 2009-08-27
I'd like to restore the dual-boot, but it doesn't "see" the ubuntu live cd. I found my xp disk and it boots up to the recovery console, but i don't know what to do from there. Should I try a similar distro, because I have another computer that can burn discs.

EDIT: Uh, no, this was a drive that I added a couple days ago. My drive with XP is recognized by the xp disc, and the FIXMBR command didn't help. I rebooted; same error.

---

### Post by Bölvaður on 2009-08-27
> **z400100500 said:**
>  and I can get to XP to recover anything.

you wouldnt be able to recover anything with xp anyway.

There are few ways, the easiest one is to install ubuntu again.

Here is your problem:

[ data | data |  data  ] This is your harddrive
[  x   |  x   | ubuntu ] This is where you put ubuntu on it
[  x   |  x   | grub   ] This is grub on your harddrive 
[  x   |  x   | deleted] This is the partition that you deleted

The boot loader isn't on the computer anymore, which is a shame but it can be helped.

SuperGrubDisk can help you do everything, it is like a cd that you can use to boot into any partition there is, or recover grub.

Setting MBR back to windows with a windows recovery disk, this will not help you too much in the long run thogh.

And as stated, the easiest thing is just installing ubuntu again.
You can even put /boot on a separate partition so this will not happen again.

---

### Post by Forbees on 2009-08-27
i'd say yourr best bet would be to reinstall Xp

and before reinstalling ubuntu you want to find a program that can recover deleted data

do a simple google search for this program, there are many of them

as long as you don't start rewriting data like no other, reinstalling xp should only write over your old xp system files, leaving all your important files unharmed

after you recover, do what you want with ubuntu, or any other distro.

---

### Post by z400100500 on 2009-08-27
so where can i get this super grub disk? I thank all of you for your help, and I'm sooooo putting ubuntu back on it. Just im gonna reformat the drive BEFORE I install it. :)

Edit: the SGD didn't work so im up a creek without a paddle.

---

### Post by JohnFH on 2009-08-27
> **z400100500 said:**
> ... then saw i only had 2 gigs of free space (should've been around 14), so i reformatted the drive it was on. 

Um, why did you do that?  That's a bit like throwing your computer out because you don't need it and then complaining to your ISP that you can't access the internet.

---

### Post by Bölvaður on 2009-08-27
I if there are no important data you lost then install ubuntu again the same way as before. But this time in the installation process (when doing the partitioning) put the windows partition as /windy, with ntfs as filesystem and do not format. Then you can make a bookmark indo your "my documents" and save everything there while you get used to things. That way you will not run out of space... this quickly.

If you lost important data:
> **Forbees said:**
> as long as you don't start rewriting data like no other, reinstalling xp should only write over your old xp system files, leaving all your important files unharmed


you can get there without installing xp at all, just use the super grub disk (well it should do that normally)

---

### Post by RaveJunkie on 2009-08-27
I agree that your actions were a bit excessive and now you could use super grub to get in or use a live disk to fix grub and use gpart to look at the hard drive rather then to format. but now that you have you can use acronis to or "get data back" to recover the data. most likely you just did a quick format and with windows it just removes the partion markers and acronis and get data back would quick fix that OR get your files at least off the xp drive. I dont know if that works for a ubuntu drive though but i doubt it.

---

