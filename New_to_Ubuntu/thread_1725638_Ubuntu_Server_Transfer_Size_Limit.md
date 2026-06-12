---
title: "Ubuntu Server Transfer Size Limit?"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by fireguy551 on 2011-04-10
I have installed Ubuntu server 10.10 and I have everything up and running but I am noticing a transfer size limitation (22gb) when I drag my files onto my network drive.

I have mapped the share folder as a network drive and it always shows 22.0 GB free of 26.3 GB.  It is a 3 TB drive.

Anyone have any ideas on how to increase the transfer size limit?

Oh my machine that I am transferring form is Windows 7 Ultimate if it is a windows problem.

---

### Post by earthpigg on 2011-04-10
meaning that you only have 26gb free on that 3tb drive?

im not sure i understand the exact nature of your setup and what is failing.

---

### Post by fireguy551 on 2011-04-10
No I have over 2.5 TB free. When I click a number of files that totals over 22gb I receive an error that says that there is not enough room on the drive. I have been transferring my files over in 21gb chunks instead of all at once.

---

### Post by HermanAB on 2011-04-10
Howdy,

When transfering large amounts of data, you should use rsync, since it will verify that everything was transferred correctly.  Read the rsync man page, it is complete with examples.

---

### Post by earthpigg on 2011-04-10
ah. that could be a nautilus file manager problem. ideally, use rsync as the poster above me pointed out.

if you love pointy-clicky, though, maybe try pcmanfm file manager (in software center). i have found that it handles crazy stuff much better than the default nautilus -- default nautilus takes 3 minutes just to open my mp3 collection's folder (it consists of about 3,000 mp3 files all lumped in one folder).

---

