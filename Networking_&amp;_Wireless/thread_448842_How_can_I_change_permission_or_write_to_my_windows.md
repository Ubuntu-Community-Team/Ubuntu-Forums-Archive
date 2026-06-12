---
title: "How can I change permission or write to my windows partition"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by waylow on 2007-05-19
Hello

I am trying to figure out how to write to my windows partition - do I need to change the file permissions? - It says the owner is the root so I can't change it

my ideal goal is to set up VMware to run a virtual machine from this partition but that it the next step

the 1st one is to figure out how I can write to this partition

can someone point me in the right direction?

thanks

waylow

---

### Post by merlinus on 2007-05-19
Have you installed ntfs-3g?  If not, you can get it from Applications/Add-Remove.

-merlin

---

### Post by timking on 2007-05-19
I would advise proceeding with caution on the ntfs-3g.  Soon after I installed it my Windows XP partition got trashed and I had to re-install.

---

### Post by dolphin_oracle on 2007-05-19
I had a folder on a fat32 windows partion that was owned by root.  it was just a folder of user created files, so I just started a root nautilus and changed the owner to my user name.  Don't know if this is the same issue for you or not.

---

### Post by waylow on 2007-05-19
THe partition is my original Windows XP NTFS file system

I don't know what nautilus is so I might give ntfs-3g a go - (thanks merlin)

but I don't want to scramble it - warning heeded (thanks Timking)

if it get scrambled I will unhappy but I won't blame myself - I can always blame Windows;)

---

### Post by dolphin_oracle on 2007-05-20
nautilus is ubuntu's file browser.  

god luck!

---

### Post by waylow on 2007-05-20
thanks for the help guys

I can now read/write to my window partition

worked out how to use nautilus and ntfs-3g

(I am still working on getting vmware to run my windows partition - but that makes me happy for now)

---

