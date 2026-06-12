---
title: "Trouble using tar"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by CompBio on 2011-01-22
This is so basic I can't believe I can't get it to work...!

I'm trying to use tar to do backups, but I've run into the $#@! /*/.gvfs problem.  The tar command keeps failing with an error whenever it reaches this file.

So, I tried using the --ignore-failed-read option as follows:

> tar cvfz --ignore-failed-read /media/backup/foo.tgz /home

But this causes tar to create a file called '--ignore-failed-read'.  So I tried it this way:

> tar --ignore-failed-read cvfz /media/backup/foo.tgz /home

Same result.  Giving up on that, I tried using the '--exclude' option so it would ignore '*/.gvfs'.  That gave me the same kinds of errors.

I'm sure I'm doing something stupid here, but I can't figure out what it is.  Ultimately I need to get my files backed up without errors!

---

### Post by coffeecat on 2011-01-22
Do you have something mounted to ~/.gvfs? If so, unmount it and try without the --ignore-failed-read option. That works for me with an empty ~/.gvfs.

---

### Post by gmargo on 2011-01-22
Try using the **--one-file-system** option.

---

### Post by CompBio on 2011-01-30
> **coffeecat said:**
> Do you have something mounted to ~/.gvfs? If so, unmount it and try without the --ignore-failed-read option. That works for me with an empty ~/.gvfs.

Thanks -- .gvfs is such an oddity that I hadn't tried to do much with it (except change permissions).  Doing umount as root was the right trick.

---

