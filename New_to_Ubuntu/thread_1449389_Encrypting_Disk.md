---
title: "Encrypting Disk"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by Sabot09 on 2010-04-07
Thank you in advance for any help offered.

Having read about encrypting my whole disk several times I confess to being lost on the subject. Is there a step by step process for me to consult? I'm running Ubuntu 9.10.

Thanks.

---

### Post by Sub101 on 2010-04-07
Do you want to encrypt the whole disk or just a few files?

If it is just a few then I would recommend cryptkeeper which can be found in the repos.

If you want to encrypt the whole disk then it is a little more complicated. A simple method is to select the "Encrypt Home" option when installing Ubuntu. As for a post installation method you'll need someone with more experience than me.

EDIT: Detail about the installation option - [http://www.ubuntugeek.com/encrypted-home-now-offerred-at-installation.html](http://www.ubuntugeek.com/encrypted-home-now-offerred-at-installation.html)

---

### Post by Sabot09 on 2010-04-07
> **Sub101 said:**
> Do you want to encrypt the whole disk or just a few files?



I'd rather encrypt the whole disk to add a level of security.

---

### Post by Sub101 on 2010-04-07
Ive always had bad experiences with full disk encryptions, however this link looks useful.

[http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html](http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html)

---

### Post by Sabot09 on 2010-04-07
Thank you.

---

### Post by Sabot09 on 2010-04-08
That didn't work very well. 

Does anyone have any advice with respect to LUKS or PGP for whole disk encryption?

---

### Post by HermanAB on 2010-04-08
I suggest that you experiment on a USB device first, till you got the hang of it.  

See this:
[http://www.aeronetworks.ca/luks-usb-howto.html](http://www.aeronetworks.ca/luks-usb-howto.html)

---

### Post by undecim on 2010-04-08
> **Sabot09 said:**
> That didn't work very well. 

Does anyone have any advice with respect to LUKS or PGP for whole disk encryption?

If you want to set up full disk encryption, the easiest thing to do is copy all your files somewhere else and reinstall using the alternate CD, which should let you set up encryption.

Though I would say an encrypted home directory and swap (which is set up if you install with an encrypted home directory) is plenty to protect from identity theft resulting from physical theft of your computer.

---

