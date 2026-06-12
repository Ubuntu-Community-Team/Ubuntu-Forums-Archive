---
title: "Putting parts of my home folder on an external drive"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Dapilot1 on 2008-12-22
So I have an external hard drive for backups and extra storage. I was wondering if there was a way to have the partition for extra space be mounted into my home folder. For instance I want my Videos, Games, and Storage folders to be on my external. But when I plug it in, i want the folders to be placed in my home folder rather than having to navigate to the external first. I think this is possible, but does anyone know how?

---

### Post by Kellemora on 2008-12-22
Hi DP1

Yes you CAN put your extra data on the external, no problem at all.

You would make what is called a SYMLINK in your home folder to the data file on your external hard drive.

It's easiest to just use Nautilus to do this, but here is the code if you want to do it via command line.

```
ln -s /path/to/real/file /path/to/non-existent/file
```

or if this makes more sense

```
ln -s filename linkname
```

filename=source linkname=target

TTUL
Gary

---

### Post by Dapilot1 on 2008-12-27
Oh, wow. That was eisier than I thought it would be. Thank you.

---

