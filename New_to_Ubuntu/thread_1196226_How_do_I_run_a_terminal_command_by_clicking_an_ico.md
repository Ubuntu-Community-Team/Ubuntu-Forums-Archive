---
title: "How do I run a terminal command by clicking an icon?"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by bakelitedoorbell on 2009-06-24
I have Warcraft2 running in Wine, which works okay.

The game needs a disk mounted for it to run.  I created a disk image, and can mount it with this command in terminal:

```
sudo mount -o loop ~/War2BNE.iso /media/iso0
```

What I want to do is make an icon that I can keep on the desktop, and double click to mount the disk image.  I have the command saved in a one-line text file.  Where do I go from there?

- Robert

---

### Post by niteshifter on 2009-06-24
Hi,

Right click on the desktop. In the menu select Create Launcher. In the Create Launcher dialog where it says Type select Application in Terminal. In the command box enter your "sudo mount -o loop ....." text that you posted here.

---

### Post by bakelitedoorbell on 2009-06-24
Cool, that worked.  I had to use the full pathname to the file.  It opens a terminal so I can type the password, then the terminal window closes and the disk mounts.

Thanks

---

### Post by Zopiac on 2009-06-24
> **bakelitedoorbell said:**
> Cool, that worked.  I had to use the full pathname to the file.  It opens a terminal so I can type the password, then the terminal window closes and the disk mounts.

Thanks

You could also make it 'gksudo ...' instead of just sudo for a nicer window asking for a password :P. At least I would prefer that.

---

### Post by bodhi.zazen on 2009-06-24
Either that or configure sudo to allow one to run mount w/o a password.

---

