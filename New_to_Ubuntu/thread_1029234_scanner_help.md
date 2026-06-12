---
title: "scanner help"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by theozzlives on 2009-01-03
"Failed to start scanner. Error during device I/O." This is the message I get when trying to scan a preview in XSANE on an Epson stylus CX-8400. Any ideas?

---

### Post by ibizatunes on 2009-01-03
[http://ubuntuforums.org/showthread.php?t=568268](http://ubuntuforums.org/showthread.php?t=568268)
the last post say they have it working 

[http://dai-videotutes.blogspot.com/2008/05/installing-epson-dx8400-on-ubuntu.html](http://dai-videotutes.blogspot.com/2008/05/installing-epson-dx8400-on-ubuntu.html)

Cant say i have one but that may help!

---

### Post by theozzlives on 2009-01-03
> **ibizatunes said:**
> [http://ubuntuforums.org/showthread.php?t=568268](http://ubuntuforums.org/showthread.php?t=568268)
the last post say they have it working 

[http://dai-videotutes.blogspot.com/2008/05/installing-epson-dx8400-on-ubuntu.html](http://dai-videotutes.blogspot.com/2008/05/installing-epson-dx8400-on-ubuntu.html)

Cant say i have one but that may help!

I already had the scanner working, but I don't know about the I/O error

---

### Post by albinootje on 2009-01-03
> **theozzlives said:**
> I already had the scanner working, but I don't know about the I/O error

Could it be a permission problem ? Are you using the same username as before ?
Check your log files (and dmesg), and : man scanimage

---

### Post by theozzlives on 2009-01-03
> **albinootje said:**
> Could it be a permission problem ? Are you using the same username as before ?
Check your log files (and dmesg), and : man scanimage

different computer, USB 1.1 instead of 2.0

---

### Post by albinootje on 2009-01-03
> **theozzlives said:**
> different computer, USB 1.1 instead of 2.0

Is your user in the group "scanner" ?
Try as your user :
```

groups

```

---

### Post by theozzlives on 2009-01-03
> **albinootje said:**
> Is your user in the group "scanner" ?
Try as your user :
```

groups

```

it wasn't but that didn't fix it

---

### Post by theozzlives on 2009-01-04
bump

---

### Post by petri on 2009-01-04
Have you seen this link [http://reformedmusings.wordpress.com/2008/12/13/fixing-epson-scanners-in-ubuntu-810-intrepid-linux/](http://reformedmusings.wordpress.com/2008/12/13/fixing-epson-scanners-in-ubuntu-810-intrepid-linux/) 

Otherwise reinstall the driver again?

---

### Post by theozzlives on 2009-01-06
bump, I REALLY wanna get the scanner working

---

