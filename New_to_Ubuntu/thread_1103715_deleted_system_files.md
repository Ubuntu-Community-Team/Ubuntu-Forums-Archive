---
title: "deleted system files"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by sailingboarder on 2009-03-23
so i was trying to clear up space on my laptop hard drive by deleting some old kernel files, assuming that my laptop was up to 2.6.27 like my desktop
turns out it wasn't, and the 2.6.27 files were remains from a intrepid beta that i no longer use
anyways, i deleted all files with *2.6.24-* from /boot /lib/linux-restricted-modules and maybe some from /lib/modules
i need to restore 2.6.24-19 files, but i don't want do a clean install if at all possible
has anyone ever done this stupid act before, and if so how can i fix it?

---

### Post by llamabr on 2009-03-23
best way to remove files is with apt.

There's a package called deborphan which is useful for finding old unused files, particularly orphaned libraries.

To your question, look in .local/share/Trash/files/

if it's not there, backup your /home, and do a fresh install.

---

### Post by sailingboarder on 2009-03-23
i have /home on a separate partition, so i am not worried about that
however, i would prefer to not have to find and reinstall every package that i have installed over the past year or so
is it possible to reinstall ubuntu while keeping track of all the new packages i have enabled?

---

### Post by hyper_ch on 2009-03-23
if the computer is still running just reinstall those packages. And you can generate a list of installed packages and have ubuntu run through it. Also the downloaded packges are saved to /var/cache/apt/archives

---

