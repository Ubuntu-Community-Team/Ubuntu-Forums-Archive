---
title: "USB 2 or 3?"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by bob brazie on 2011-03-03
Is there a command to show whether the usb ports in my new laptop are 2 or 3?

Visually I can't tell.There is nothing in the documentation showing this. Somewhere I saw a web video of this machine that "might" have mentioned 3.0.

Thanks in advance. bob.

---

### Post by turtle153 on 2011-03-03
Get the package hardinfo```
hardinfo
``` and find your motherboard part number. Search this on the manufacturer site and look at the specs.

---

### Post by An Sanct on 2011-03-03
USB 3 has a blue connector (the plastic inside) and might be slightly different shape.

---

### Post by turtle153 on 2011-03-03
Run ```
lsusb -v
``` and look for "idProduct", the version number will be next to it. Remember that there might be a mix of 1.1 and 2.0.

---

### Post by bob brazie on 2011-03-03
Apparntly it is 2.0? Does Ubuntu 10.10 support 3.0?

---

### Post by NCLI on 2011-03-03
> **bob brazie said:**
> Apparntly it is 2.0? Does Ubuntu 10.10 support 3.0?  
USB 3.0 works just fine for me.

---

### Post by An Sanct on 2011-03-04
AFAIK support for 3.0 was out as soon as the documentation for it was ready :)

PS. please bob brazie edit your post and put the extra long copy and paste into a **[CODE] **section (the **#** button in the editor) ... such posts are unreadable

---

### Post by mcduck on 2011-03-04
Linux was the first operating system to provide support for USB3.

And, like mentioned, the connectors are easy to detect as they are, by standard, colored blue. (the shape is also slightly different but that might be hard to spot without comparing the port to an older one, and anyway the color is a clear sign on its own)

---

### Post by bob brazie on 2011-03-04
I still can't tell. <g>

Does this help?

---

### Post by An Sanct on 2011-03-05
I'd say, those are USB2.0 (also according to the small icons beneath them)

But here's a better explanation, look at the attached image, there you will see 8 usb ports, 2 of them are (or have the capability to be*) 3.0

the black ones are 2.0
the blue ones are 3.0

Also take a look at this:

USB 2 logo
[IMG]http://i1.squidoocdn.com/resize/squidoo_images/50/lens8129061_1258569962usb-logo.jpeg[/IMG]

USB 3 (Super Speed)  logo, please don't mind the thumb drive there.
[IMG]http://www.grazeit.com/thumbs/fid1/everythingusb.com.super_talent_supercrypt_flash_drives_news.jpg[/IMG]

Anyhow, if your computer has USB 3 support, there has to be a big 3cm*3cm logo on it, stating, that it does ;) (Like the designed for wins and I3/5/7 logo I managed to see on your picture)

---

