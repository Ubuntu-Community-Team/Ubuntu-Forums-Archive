---
title: "mount.cifs ioencoding error"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by ic3000 on 2008-07-14
Hi to all,

I'm using a script that uses mount.cifs to access a share on a w2k3 server, and it works but i still have a problem here!

When using mount.cifs on ubuntu i get in some sirectory and files a codification error for special characters like ~, ç etc...

If i use smb://servername/sharename to access the share on the w2k3 server i can see all the files and folders with proper charset encoding but when i tried to use mount.cifs i finish with the enconding problem for special characters...

Is this a problem or limitation with mount.cifs on Ubuntu?

I tried to use iocharset=utf8 and iso8859-a but the result is the same...

The same script using sbin/mount.cifs on fedora i get the right enconding...

the command i use is mount.cifs //servername/sharename /localdirectorytomountshare

Any clue on what could be wrong here?

Thanks again!

---

### Post by teeros on 2008-08-12
I am also suffering from this problem. Have you made any progress in this matter?

---

### Post by SergeiFranco on 2008-12-03
I have same problem.
this is kUbuntu 8.04 I am talking about.

When I browse the network (smb:\\) it shows Cyrillic characters fine. When I try to mount the following happens:
if I specify iocharset=utf8 it shows funny characters (twice as much as normal) instead of Cyrillic (a lot of characters look like "D" with some lines added to it).
If I don't specify iocharset it would show Cyrillic characters as "?", but they appear to be right length.

What shell I do?

---

### Post by CHaoSlayeR on 2009-02-05
Hi there,

I had the same problem but for me this one worked:

```

sudo mount -t smbfs -o credentials=/root/.smbcredits,nounix,dir_mode=0755,file_mode=0644,iocharset=utf8 //sheela/Dokumente /net/sheela/Dokumente

```

But I am on a Kubuntu 8.10, so maybe there may be another version of mount.cifs? DPKG says: ```
2:3.2.3-1ubuntu3.4
```

In addition Unicode is based on 16bit per character so it may be an option to try utf16 as well.

C]-[aoZ

---

