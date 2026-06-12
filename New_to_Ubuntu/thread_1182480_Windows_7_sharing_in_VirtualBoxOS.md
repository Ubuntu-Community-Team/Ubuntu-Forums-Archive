---
title: "Windows 7 sharing in VirtualBoxOS"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by sevenones12 on 2009-06-09
I'm trying to figure out how to get a shared folder to work on the VBoxOSE using Windows 7. From what I gather, I had to create a shared folder and map the drive as \\vboxsvr\shared . The drive still isn't being found. Any help would be greatly appreciated.

---

### Post by keplerspeed on 2009-06-09
[http://www.ideaexcursion.com/2009/01/15/windows-7-in-virtualbox-shared-folders-workaround/](http://www.ideaexcursion.com/2009/01/15/windows-7-in-virtualbox-shared-folders-workaround/)

---

### Post by sevenones12 on 2009-06-09
When it says the "host computer" name. What would I put for that?

---

### Post by keplerspeed on 2009-06-09
Your host is the ubuntu install. So whatever you called your computer when you installed ubuntu. It will be you@hostname:~$ when you open a terminal.

---

### Post by sevenones12 on 2009-06-09
Thanks alot man. I got it to work. My guest account wasn't installed correctly, and the hostname worked.

---

