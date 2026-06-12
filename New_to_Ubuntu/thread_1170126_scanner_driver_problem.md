---
title: "scanner driver problem"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by Jasper7g on 2009-05-25
I have downloaded a driver hopefully for a HP Scanjet G2410 scanner. When I click on Xsane Image Scanning Program I get the following message: "Failed to open device 'v4/:dev/video0' " So presumably I'm not going to have any joy. Is there any way I can get my scanner to work on Ubuntu?

---

### Post by Zimmer on 2009-06-14
Cannot find it on the SANE site as supported.....  
[http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD](http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD)

---

### Post by sandyd on 2009-06-14
> **Jasper7g said:**
> I have downloaded a driver hopefully for a HP Scanjet G2410 scanner. When I click on Xsane Image Scanning Program I get the following message: "Failed to open device 'v4/:dev/video0' " So presumably I'm not going to have any joy. Is there any way I can get my scanner to work on Ubuntu?
the scanner should be looking in /dev/video0, not v4/:dev/video0.

look around in /etc/sane.d and see if you can find where the error was made

---

