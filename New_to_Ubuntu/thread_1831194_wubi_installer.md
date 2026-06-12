---
title: "wubi installer"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by callmebat62 on 2011-08-23
Hey all,

I'm new to Ubuntu, I'm finishing up a degree in IT and the current class I'm in is beginning Unix so I wanted to try Ubuntu since I've heard a lot about it lately. I downloaded the wubi installer, everything I've read about it indicates it's fairly easy to use but I'm getting an error message when I try to use it.  

The error message reads "There is no disk in the drive. Please insert a disk in to  drive \Device\Harddisk2\DR2."

I might be missing something, I'm not sure, but I was under the impression that this worked like a regular Windows installer, any advice?

---

### Post by mintpenguin20 on 2011-08-23
I would just remove wubi , and install virtualbox with virtualbox you can run ubuntu in a virtual machine so you can run it in windows itself . 

Here is a link to virtualbox [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

click on the windows host for windows installer .

here is a link for instructions on how to install ubuntu in virtualbox 
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by bcbc on 2011-08-23
> **callmebat62 said:**
> Hey all,

I'm new to Ubuntu, I'm finishing up a degree in IT and the current class I'm in is beginning Unix so I wanted to try Ubuntu since I've heard a lot about it lately. I downloaded the wubi installer, everything I've read about it indicates it's fairly easy to use but I'm getting an error message when I try to use it.  

The error message reads "There is no disk in the drive. Please insert a disk in to  drive \Device\Harddisk2\DR2."

I might be missing something, I'm not sure, but I was under the impression that this worked like a regular Windows installer, any advice?
This is a longstanding bug due to the way python (or rather the wubi usage of python) handles drives that are assigned but empty. e.g. MMC readers. Generally there is some peripheral device that is triggering an exception. You can either click through it (many times) or try to unplug unnecessary devices (phones, usb, printers etc) and see if that resolves the issue.

---

