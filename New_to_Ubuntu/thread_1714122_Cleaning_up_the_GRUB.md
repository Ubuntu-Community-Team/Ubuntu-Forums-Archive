---
title: "Cleaning up the GRUB"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by daddy0h on 2011-03-24
Installed in a dual boot Win XP and Ububtu 10.10. 
All is fine.
Grub shows these options for booting up:
ubuntu 10.10 (this is abridged of course) 32.22 (or something like that)
ubuntu safe mode
mem test
Windows XP

Then I did an update
Grub shows

Ubuntu 10.10 32.28(or something like that)
ubuntu safe mode
mem test
ubuntu 32.22 
ubuntu safe mode
mem test
Windows XP

So... as you can see... the GRUB is growing. I would like to keep the GRUB clean so it doesn't get confusing. I tried using the System cleaner but it did not clean the grub. I can boot up to the version before the update and I understand it is great to have the previous version as a backup, but i have been working with the updated version just fine and, because my HDD is not very large, now that i feel safe I would like to get rid of that version (and its GRUB entry).

How can I do this in a safe way? Any help (in as layman terms as possible) would be appreciated.

Daddy0h

---

### Post by ~Plue on 2011-03-24
older kernels doesn't take much space on the drive.. 
but if you want to remove them, search synaptic for the package and remove it. or you could use [ubuntu tweak ]("http://ubuntu-tweak.com/")

both methods are explained in detail here >> [http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

---

### Post by daddy0h on 2011-03-25
Cool!!!! Will give it a shot!!!!

---

### Post by daddy0h on 2011-03-25
Ok... i got the Ubuntu tweak utility. When I try to uninstall the unused kernels it asks me for a Password that allows me to do administrative tasks in essential parts of my system... my admin password is not accepted... i am thinking it is asking for the root password... where can i find that?

---

### Post by daddy0h on 2011-03-26
Well... this is what i did... i changed my Administrative privileges from custom to Administrator for my Admin profile (I use mostly my desktop user profile). That allowed me to do what I needed to do. Still need to learn about the inner workings of Ubuntu... any books recommended for it?

---

### Post by goldblattster on 2011-03-26
Well, there's the [official ubuntu book]("http://www.amazon.com/Official-Ubuntu-Book-Benjamin-Mako/dp/0137081308/ref=sr_1_1?ie=UTF8&qid=1301115161&sr=8-1")...

---

