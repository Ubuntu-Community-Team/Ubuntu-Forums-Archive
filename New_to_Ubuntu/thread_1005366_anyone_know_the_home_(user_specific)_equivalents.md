---
title: "anyone know the /home (user specific) equivalents?"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-12-08
I do a lot of fresh installs (cyberchondria) so I'm wondering what the home versions of these config files are.

I am the only user so the home directory is enough for me.

/etc/modules.conf
/etc/modprobe.conf
fstab maybe??


Anyone know of anymore I may have forgotten which are used often?

Thanks in advanced!!

---

### Post by mapes12 on 2008-12-08
> /etc/modules.conf
/etc/modprobe.conf
fstab maybe??

Unless your system has broken then you don't need to worry about these.

Not sure what your asking but /home will contain all your personal settings, bookmarks, files and the like. Many of these files are hidden. If you want to see them Places>Home Folder then Ctrl+h will bring them up. Ctrl+h again will make them invisible again.

---

### Post by linux6994 on 2008-12-08
Just a thought - A real simple straight forward way of backing up those settings is sbackup. It will allow you to backup your entire /home/directory for safe keeping. I backup mine every night at midnight to a USB drive. sbackup has two functions - one backup, two restore.

Hidden file example:
I use virtualbox for other OS playing like XP, or Fedora, or SUN. All of your virtual machines are stored in .virtualbox one of the hidden file directories. Once the machines are created then you can swing the .virtualbox file out to another pc, it saves time in rebuilding it basically coping it.

---

### Post by mcduck on 2008-12-08
> **pluckypigeon said:**
> I do a lot of fresh installs (cyberchondria) so I'm wondering what the home versions of these config files are.

I am the only user so the home directory is enough for me.

/etc/modules.conf
/etc/modprobe.conf
fstab maybe??


Anyone know of anymore I may have forgotten which are used often?

Thanks in advanced!!

Since all these files are related to system configuration, there are no user-based configuration files at all. (per-user configuration of kernel modules, for example, simply wouldn't work.)

If you need to change file system mounting or loaded modules use the files in /etc. If you reinstall often you should just take backups of these files.

---

