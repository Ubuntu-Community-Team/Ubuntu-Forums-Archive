---
title: "Sharing With Ubuntu"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by zunebuggy on 2010-04-21
I have a few PCs running Windows XP in my home network. A friend recently gave me a PC he was throwing out and I have decided to make it strictly Ubuntu.  I would, however, like to have one folder on this Ubuntu machine shared with the XP machines.  I understand the file system is not even the same between Ubuntu and XP... Is it possible then to make one folder shared.  My thought is to be able to share documents and pictures between the Ubuntu machine and the XP machine machines.

:confused:

---

### Post by ed-koala on 2010-04-21
You will need to make an NTFS partition on the machine and put the files to be shared there so Windows can see it.  Windows can't read any Linux formats.

---

### Post by undecim on 2010-04-21
> **ed-koala said:**
> You will need to make an NTFS partition on the machine and put the files to be shared there so Windows can see it.  Windows can't read any Linux formats.

The filesystem has nothing to do with sharing files over the network. If you were using an external drive, then yes, you would need to use NTFS.

If you are sharing over the network, you should be able to right-click on a folder and choose the "share" option (it's been a while since I've used the default Ubuntu file manager, but I think that works)

Your Ubuntu computer should then show up on the Windows network with a share for that folder.

---

### Post by zunebuggy on 2010-04-21
Oh, so Ubuntu can't see a share on Windows XP and vice versa?  It's not a big deal.  I just thought maybe there was a 3rd party application for Linux that allowed it. It's probably not a good idea anyway with all of Windows XP security issues....

---

### Post by zunebuggy on 2010-04-21
Sorry replied before I saw the last reply. Cool! Sounds like it can be done then.

---

### Post by Iowan on 2010-04-21
Samba is used to share files between Windows and Ubuntu (Linux). Ubuntu comes with the client pre-installed, but to share from Ubuntu to Windows means installing the Samba server. More details if you wish...

---

