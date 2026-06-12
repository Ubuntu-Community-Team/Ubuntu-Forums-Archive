---
title: "Where are SMB shares mounted??"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by SpazTheCat on 2008-04-22
Hi,

I have a silly question. Where are SMB shares really mounted in Ubuntu 7.1? I can connect to the windows shares I routinely use and there is now a folder on the desktop representing the share. But, I'd like to use rsync to sync one of the shares with a local directory but when I look on the path "~/Desktop/sharename" there is nothing there. Not even the shares are listed in a terminal if I look in "~/Desktop".

I looked in /mnt and /media but there is nothing there either.

Thanks,

Andy

---

### Post by superprash2003 on 2008-04-22
you have to mount it manually .. using the smbmount command

---

### Post by blastus on 2008-04-22
You should be able to access them from Places->Network. Select the host name of your server and then you'll see all the shares. If you double click on a share it will mount it. You may find you have to reboot if the shares or your server don't show up.

---

### Post by Diabolis on 2008-04-22
I think that the question is:
how can you access those folders through the command line?

And if not, I would like to know hehe.

---

### Post by hosammy on 2008-04-23
> **superprash2003 said:**
> you have to mount it manually .. using the smbmount command

I have a similar question, I know how to mount manually in smb://chamber/ which is the other windows network's name. May I know how can it be auto mount when I login the unbuntu? Which file I need to edit?

Regards ...
:mad:

---

