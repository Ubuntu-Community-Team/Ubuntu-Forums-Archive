---
title: "Need help scanning documents"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by Mooble on 2009-11-19
I've got an Epson NX400 all-in-one printer/scanner/copier.  Printing worked out of the box, but I need to scan some documents.  I tried using xsane, and it told me it couldn't find any devices.  I then installed a driver from _[here](http://avasys.jp/eng/linux_driver/)_, but xsane still finds nothing.

---

### Post by lindsay7 on 2009-11-19
See if this helps,

[http://ubuntuforums.org/showthread.php?t=944778](http://ubuntuforums.org/showthread.php?t=944778)

---

### Post by Mooble on 2009-11-19
No, that's where I got the idea to install the drivers I linked to.

However, it turns out I was missing a package, which I found for 8.10, but not for later releases...
[http://packages.ubuntu.com/hardy/libltdl3](http://packages.ubuntu.com/hardy/libltdl3)
I went ahead and installed it, and it works.  Is there a chance having that lib installed will break something else?

---

### Post by lindsay7 on 2009-11-19
I would run sudo apt-get update and sudo apt-get upgrade and see if it will update your files for this

---

### Post by Mooble on 2009-11-19
Well, I ran those commands and it listed a few other packages, but not libltdl3.

Also, it seems when I try to save the images I scan, I can't open them.  I get a "failed to open input stream" error.

---

### Post by lindsay7 on 2009-11-19
did you find this page,


[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

---

### Post by Mooble on 2009-11-19
That link takes me to the Chinese/Japanese homepage (I think?).  Can't read it.  =X

---

### Post by lindsay7 on 2009-11-19
This is what I get,

[ATTACH]136892[/ATTACH]


This is how I got there.

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

---

### Post by Mooble on 2009-11-19
Yes, that new link works.  And yes, I went through that page while downloading the driver.

Just found the program they installed along with it, called "Image Scan!".  It says it "cannot send command to scanner" when I run it.  Xsane at least nabs an image and displays it for me.  It just saves junk rather than a file.

I looked through their troubleshooting section, didn't find anything useful.  (I may just such at searching...)

---

### Post by lindsay7 on 2009-11-20
Well, I am out of ideas.

---

### Post by Mooble on 2009-11-20
Thanks for trying to help =)

---

