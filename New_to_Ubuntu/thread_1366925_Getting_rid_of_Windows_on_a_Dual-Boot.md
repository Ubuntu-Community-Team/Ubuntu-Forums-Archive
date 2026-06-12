---
title: "Getting rid of Windows on a Dual-Boot"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by SPazzo on 2009-12-28
Hi!  So I have Ubuntu 9.04 and Windows XP dual-booted on my MSI Wind netbook.  I bought this netbook to use Ubuntu only, but I decided to dual boot for a while anyway.  I now want to I guess wipe the Windows partition, but keep the Ubuntu partition untouched.  I know I can just re-install Ubuntu over everything, but I've installed a lot of stuff, and it would kinda be a pain to have to re-install everything and back up all the stuff I have on there.

Is there anyway to just get rid of the Windows partition?  Will GParted do this?

---

### Post by Mahngiel on 2009-12-29
yes it will. you don't even have to boot to the live cd. if you don't have GParted, you can 'sudo apt-get install gparted' and then 'sudo gparted' and delete the partition it sits on.

you would want to boot from the livecd though, afterwards, in order to move your ubuntu partition to the beginning of the hard drive so you can extend it for more space.  this can be a bit hazardous, so i'd recommend backing up everything before you tried it.

bear in mind... the word "partition" should invoke the words "back up" into your noggin. :)

---

### Post by SPazzo on 2009-12-29
Mmmkay.  I assume you mean a GParted live CD.  Is there a way to run that from a USB flash drive?  Like a Unetbootin kinda deal?

---

### Post by Mahngiel on 2009-12-29
yes, you can get a liveusb/cd for gparted, you'll have to google the link. it would be much faster than, say, running the ubuntu livecd - that takes forever to boot.

---

### Post by SPazzo on 2009-12-29
OK, great!  I'll be doing it tomorrow.  If I have any more questions, I'll post them.  ;-)

Thanks!

---

