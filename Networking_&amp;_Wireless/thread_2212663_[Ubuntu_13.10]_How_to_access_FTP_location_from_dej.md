---
title: "[Ubuntu 13.10] How to access FTP location from deja-dup folders"
date: 2014-03-22
forum: Networking &amp; Wireless
---

### Post by actionmystique on 2014-03-22
Hello,

I've connected my laptop to FTP locations from Nautilus and installed bookmarks. I cannot do the same if Nautilus is run as root.
When I access deja-dup as root, these bookmarks/links do not show up. It probably has something to do with the fact that Nautilus was not run as root.

Any idea on how to accomplish this?

---

### Post by houstonbofh on 2014-03-23
When you are root, your config files are stored in /root...  You will need new ones.

---

### Post by actionmystique on 2014-03-23
> **houstonbofh said:**
> When you are root, your config files are stored in /root...  You will need new ones.

Could you please elaborate?

---

### Post by houstonbofh on 2014-03-23
Look in your home directory.  Now show the hidden files...  Those are config files for everything from your default settings in your music player, to the icons in your menu bar.  If you create a new user, they will have different config files.  The root account is also a new user.  While your directory is under /home/username the root account is under /root so you can either copy all of your config files there, or just make new bookmarks.

---

### Post by actionmystique on 2014-03-24
I don't follow you: it is not possible to connect to FTP servers from nautilus if it is run as root. Changing its config files does not change this strange behavior: [https://docs.google.com/document/d/11oEMIO600mMUJ5h_K_3LlCXqC3WDMA-NnR5Fj7D2p1k/edit?usp=sharing](https://docs.google.com/document/d/11oEMIO600mMUJ5h_K_3LlCXqC3WDMA-NnR5Fj7D2p1k/edit?usp=sharing)

---

### Post by houstonbofh on 2014-03-26
Ah...  OK.  I misunderstood what you are doing.  You are trying to make gvfs (Gnome virtual sile system) mount a remote file system from an account that is not actually running.  That does not work.  You can also not do it if you su to an actual account, as it runs through your desktop environment, not just the running application.  There may be ways to hack this, but I do not know any.

---

### Post by actionmystique on 2014-03-27
Actually, it is possible to FTP from Nautilus,** as long as it is not launched as root** (on this screenshot, "root" is the FTP account name on remote device): [https://docs.google.com/document/d/1o0fEH9UKIZO2hYZiMEzB3vsGdoga44Ko0n_Z3j7L-tM/edit?usp=sharing](https://docs.google.com/document/d/1o0fEH9UKIZO2hYZiMEzB3vsGdoga44Ko0n_Z3j7L-tM/edit?usp=sharing)

---

