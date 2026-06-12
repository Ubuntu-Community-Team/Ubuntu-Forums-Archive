---
title: "deleting files in mounted smb file system"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by Mouloud on 2007-08-25
Hi,

I mounted a smb filesystem with pam_mount using:
```
volume * smbfs linkserver Musique /home/&/Musique dmask=770,fmask=770,iocharset=utf8,uid=&,gid=&,credentials=/home/&/.pam.cred - -
```

The share is mounted allright, I can create, read, rename files, but when I want to delete a file, it says I don't have permission to move it to trash. I can delete files through the console though (not through the trash).

Here is my question: I don't want to use the trash for these files (when I delete a distant 500mo file, it would move it locally to put it in the trash, right? it sucks!!).
Can I configure something so the distant files get deleted right away?

Sorry if I'm not precise enough, I'm no native english speaker.

---

