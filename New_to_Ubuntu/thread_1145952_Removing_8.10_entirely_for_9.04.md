---
title: "Removing 8.10 entirely for 9.04"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by Anonono on 2009-05-02
I started off with 8.04, and then upgraded it to 8.10 without any problems whatsoever. But I want to remove it and start fresh with 9.04, because I basically messed up my Ubuntu (Prior to 8.10, I think). Mainly, I installed KDE, which leaked a bunch of programs across to Ubuntu that I'm too scared to remove. The Wireless connection program doesn't work correctly (But I can still get a connection), Flash isn't recognized across all of my browsers for some reason, there's a bunch of themes I can't remove, etc.

I'd rather start with a fresh Ubuntu system than uninstall all the crap and then upgrade, so how could I do this easily? I run it in a dual-boot with Windows XP, so I don't just want to format, and I understand that removing Ubuntu may also erase GRUB, and therefore I wouldn't be able to get into XP.

So how can I do this safely?

---

### Post by stretch427 on 2009-05-02
If you have your /home residing on a separate partition than your root (/) partition, you could just wipe the root partition and install it on that.  If done correctly you should keep all your files just not the base system.

Just an warning, **BE CAREFUL**!

I've done this incorrectly and lost 100's of GB worth of media.

Other than that I don't know if you can just start from scratch without wiping something. 

Please take my advice with a grain of salt. 

Cheers!

---

### Post by stretch427 on 2009-05-02
I didn't see some of your edits sorry.

---

### Post by theozzlives on 2009-05-02
When you get to the partitioning section, whether you have a seperate /home or not, choose manual (advanced). On your / (root) partition choose edit and make it ext4 or ext3, check the format box, and mount point is /.

If your /home is seperate, edit it, ext3, DON'T FORMAT, mount point is /home. If you don't have a seperate /home you'll have to backup anything you don't want to lose.

---

### Post by Anonono on 2009-05-02
i don't have a seperate Home folder, and all my files can be backed up onto a memory stick.

So, do I just burn a 9.04 disc, install it and overwrite 8.10?

---

### Post by bumanie on 2009-05-02
That will work fine. You can choose to make a separate /home during the new installation if you wish, but that is up to you. Back up any files you need first.

---

### Post by zeroseven0183 on 2009-05-02
Excuse me. How did you install Ubuntu? Was it an installation inside Windows?

If it is, you may consider uninstalling it under Add/Remove Programs. I also dual-boot and my default OS is Ubuntu. Once you uninstall it inside Windows, you will have to change the content of boot.ini.

Backing up your files needs to be the first thing to do just what the three of them said.

---

### Post by Spiritous on 2009-05-02
> **zeroseven0183 said:**
> Excuse me. How did you install Ubuntu? Was it an installation inside Windows?

If it is, you may consider uninstalling it under Add/Remove Programs. I also dual-boot and my default OS is Ubuntu. Once you uninstall it inside Windows, you will have to change the content of boot.ini.

Backing up your files needs to be the first thing to do just what the three of them said.

Hmm?

> I run it in a dual-boot with Windows XP, so I don't just want to format, and I understand that removing Ubuntu may also erase GRUB, and therefore I wouldn't be able to get into XP.

---

