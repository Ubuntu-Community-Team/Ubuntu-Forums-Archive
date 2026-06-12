---
title: "help unpacking zip to website"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by eastenergy on 2010-01-07
Hi all :)
As it says on the label, I would like to unpack a zip on my website using the command line...
normally Id search for hours for the answer myself (I learn a lot more that way) but Im kinda running today.
Thanks!

Oh...by the way Im on Ubuntu9.04

---

### Post by dmaxel on 2010-01-07
I googled around a bit and came with this:

sudo apt-get install unzip

Then go to the directory with the zip...

unzip FILENAME.zip

If you use Ubuntu Desktop, you should try to use the graphical interface to do so. Also, if you can FTP with another computer, you can unzip with that extra computer and upload the unzipped content.

---

### Post by Cheesemill on 2010-01-07
This all depends on whether or not you have shell access to your server.
If you do then it's as simple as running:
```
 
unzip filename.zip

```
If you don't have shell access (which is usually the case with web hosts) then you should unzip the file on your machine before uploading the resulting directory to your server.

---

### Post by eastenergy on 2010-01-07
Seems the bast way is to unzip and transfer....but its a large file... and crappy hosting

Thanks for the quick hosting

---

### Post by lisati on 2010-01-07
Are you hosting the website yourself?

As others have suggested, you could always use the graphical interface to unzip before copying the contents.
If it's another machine on your own home network, you could use something like ssh to log in to the other machine via the command line and upzip the file from there.

If someone else is hosting the web site, it's probably easier to unzip the file first before copying it, as running stuff on someone else's machine raises an issue of getting the other person's permission.

---

