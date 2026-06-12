---
title: "Nautilus SMB share from console?"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by Kleenux on 2008-05-29
I mounted a SMB share from Nautilus.

Now, I want to work with the share from the console, but

- no trace of the share in the 'mount'
- no trace of the share in the whole files tree


Where does Nautilus attach the SMB share so that one can work on it directoy from the console?

---

### Post by dmizer on 2008-05-29
nautilus does not mount the share, it caches the share through the gnome-vfs.  this means that anything mounted by [places > connect to server] will only be available to parts of the os which are aware of nautilus.

so, things like vlc, open office, rhythmbox, and many other popular packages, cannot see the share.

the only way i am aware of to correct this, is to mount via the command line in /etc/fstab.  if you are interested in correcting this problem via the command line, please see the second link in my sig.

---

### Post by krisek on 2008-07-10
with the appropriate gnome-vfs command line utilities you can do a lot from the text based shell

---

