---
title: "Flash drive?"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by XKCD64 on 2009-08-16
Hi, I have a question.  I want to use an 8-16GB flash drive as a hard disk.  Is it possible to install Ubuntu on the flash drive (Just as if it was a normal hard drive, not an install image), and to boot from that flash drive to work in ubuntu.  And saving files and everything would work ok??  So like, I would be just like a small hard drive?

How do I do this?

---

### Post by Katalog on 2009-08-16
I would imagine you could just boot up from a Live CD with the USB drive inserted in your computer, and then when you go to install Ubuntu and it asks where you want to install it, you just choose the thumb drive instead of your hard drive. I've never tried anything like that, but I don't see why it wouldn't work. You know you can also create a persistent Live USB that will do basically the same thing.

---

### Post by MelDJ on 2009-08-16
you can do it. u must do a persistent install to enable saving of settings etc. try going to pendrivelinux to learn how to do it

---

### Post by theozzlives on 2009-08-16
I did an install once, I disconnected my hard drive so it wouldn't mess with the boot sector. I think it takes 3.3 GB to install, that's not counting documents, updates, and other software.

---

### Post by Wim Sturkenboom on 2009-08-16
I don't have experience with it. However be aware that flash drives have a limited number of write cycles for a location (I think nowadays it's around a million). This has two implications:
1)
Use a non-journaling filesystem (e.g.ext2)
2)
Flash drives are not suited for data that is modified often. This can be files that you're editing but also Linux keeps track when a file was last accessed by writing some data (I think in an inode, not sure). The latter can be prevented although I'm not sure how (the system that I'm tyoing this on has only limited info pages, but I think it's a mount option (noatime?)).

PS I'm going to try something like this soon for my Aspire One.

---

### Post by ArmenianLeader4 on 2009-08-16
It is possible, although you would need the ISO image on a Live CD, and you had better watch out. I tried to install Linux on my external HDD and it corruptted the files on my internal one... not sure why, but it could be a recurring glitch on alot of computers.

---

