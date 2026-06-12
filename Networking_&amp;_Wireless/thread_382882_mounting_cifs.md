---
title: "mounting cifs"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by rvdb on 2007-03-12
I have a Maxtor Shared Storage II Nas. I have great problems mounting it from Linux (Ubuntu Efty).

- using CIFS i cannot change the write permission and thus i can't make a file executable

- when usign smbfs every file in executable (i hate that...) and more importantly i cannot make symbolic links.

Could anyone shed some light on these troublesome matters?

E.g. what is your mount command line (or fstab entry) to use a cifs NAS (or smbfs) to let the drive behave as much linuxish as possible.

With kinds regards
Rein van den Boomgaard

---

### Post by Frosty Cold Drink on 2007-03-13
CIFS/SMBFS do not usually do UNIX-style file permissions, since the file systems they were designed to share originaly didn't even have file permissions. There are UNIX extensions to CIFS, but chances are your NAS is using FAT32 as a file system and doesn't have these extensions.

Perhaps someone has some decent work-arounds for you but as far as I know you are stuck. You can use file_mode and dir_mode when mounting CIFS to set the permissions for all files and directories on the filesystem when mounted. As risky as it is, you may want to have everything on the filesystem executeable if you *have* to have something executable. If you are talking about interpreted sccripts, you may want to just invoke the interpreter directly.

---

