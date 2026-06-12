---
title: "rar protected  files"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by dacoch on 2010-09-14
How can I compress a .rar file but I want to:
- archive it in 98MB parts
- protect it with a password
- use maximum compression

that can't be done with archive manager only through terminal but when I type this:

$ rar a -hp -v100352k compressedArchive.rar -r (list of archives)

it prompts me for a password but it doesn't archives it in diferent volumes

---

### Post by jtarin on 2010-09-14
[I know how you like to read so...]("http://www.technologyquestions.com/technology/linux/111133-how-create-multipart-rar-archive-linux.html").

---

### Post by asmoore82 on 2010-09-14
I would avoid rar at all costs - proprietary bloatware.

There are free archive formats - ar, tar, 7z.
There are free compression methods - gzip, bzip, lzma.
There is free and more secure encryption - GPG.

Multi-part archives are a cheap trick - split/cat can do this to _any_ file of _any_ type.

Rar has absolutely nothing to offer.

---

### Post by dacoch on 2010-09-15
> **asmoore82 said:**
> I would avoid rar at all costs - proprietary bloatware.

There are free archive formats - ar, tar, 7z.
There are free compression methods - gzip, bzip, lzma.
There is free and more secure encryption - GPG.

Multi-part archives are a cheap trick - split/cat can do this to _any_ file of _any_ type.

Rar has absolutely nothing to offer.
I know but I want to upload it so some friends can decompress it, and I haven't been able to introduce them into the world of linux... they use winrar even though it's prett lame

---

### Post by jtarin on 2010-09-15
7zip supports most of these listed archives as does Winrar. Both applications run in Windows and both can be used in Linux. There is a Rar in the repositories that is non-proprietary, but 7zip is free and runs on both machines. 7zip does recognize, open and create rar files but that's all. It doesn't allow you to add or remove files in the rar

---

