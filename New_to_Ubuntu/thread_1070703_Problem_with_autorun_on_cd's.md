---
title: "Problem with autorun on cd's"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Drenriza on 2009-02-15
Now this must be absolute beginner talk :KS

But when i try to install wow (for example).
It cannot find the auto-run application. Anyone with an idea why?

Kind regards
Drenriza

---

### Post by ithanium on 2009-02-15
The autorun on an original WoW copy is a .exe file
Ubuntu can't run those files, as they are made for Windows

If you want to play WoW on an Ubuntu System you will need to see more about Wine [here]("http://www.wowwiki.com/Wine")

---

### Post by geirha on 2009-02-15
You probably have a newer WoW install DVD. The DVD contains files for installing on both Mac and Windows. If you insert the DVD on a Mac though, the windows specific files are hidden, and if you insert it in Windows, the Mac specific files are hidden. It has probably been mounted as a Mac DVD, so you're not seeing the windows files (which are the ones you want to use).

The World of Warcraft page on the wiki has instructions on how to bypass this: 
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
> 
**Note** that on some WoW DVD's the installer executable is hidden and you need to re-mount the disc with the 'unhide' option. To do this type in a terminal:

```

  sudo umount /dev/cdrom
  sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/

```


---

### Post by Drenriza on 2009-02-15
Thanks a lot, I can now see the cd along with the exe file.

Can you do like this every time you can't mount the cd probably? or only with wow

Thanks on advance.

---

