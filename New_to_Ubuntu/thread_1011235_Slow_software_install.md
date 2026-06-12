---
title: "Slow software install"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by moonscapex on 2008-12-14
Hi,
I just installed the newest version of Ubuntu and decided to do my updates immediately.  There were 160 and it took about 4 hours.  Also, installing software is very slow.
My Internet connection is usually around 300kb/s (in Firefox).  Downloading software in the package manager has about 24kb/s.

How can I speed it up?

---

### Post by oldos2er on 2008-12-14
Try a different server? System, Administration, Software Sources, Download From....

---

### Post by Michael.Godawski on 2008-12-14
hi moonscapex, 

how are you connected to the internet? Via wlan or wired? or anything else.. :p

---

### Post by moonscapex on 2008-12-14
I'm Wired

---

### Post by jbrown96 on 2008-12-14
The repositories may just be busy. Is the connection running at full speed otherwise (i.e. internet sites)? What repositories are you using and what is your location (country)? In a terminal, could you copy and paste the output of ```
cat /etc/apt/sources.list
``` I always mess this up. It's either "sources.list" or "sources.lst". If you don't get anything try changing the filename.

---

### Post by OutOfReach on 2008-12-14
I would do as oldos2er suggested, different servers may have faster download speeds than the one you are using (which I'm guessing is the default)

---

### Post by moonscapex on 2008-12-14
My connection is running at full speed in the internet.
I am using the main Canadian repository.

---

### Post by moonscapex on 2008-12-14
I found the server from my city, maybe that will work.

---

### Post by moonscapex on 2008-12-14
I tried the main server. Its almost my full Internet speed.  Thanks for the help.

---

