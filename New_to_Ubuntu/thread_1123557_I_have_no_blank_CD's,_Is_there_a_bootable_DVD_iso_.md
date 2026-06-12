---
title: "I have no blank CD's, Is there a bootable DVD iso for 9.04??"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by dekerf on 2009-04-12
I couldn't find a dvd image on the download page. Is it possible to turn the CD iso image a DVD iso image?? Heh, the only reason I've ever bought blank CD's the last couple years is to burn Ubuntu images, might be time to start releasing DVD iso's as well.

---

### Post by linux_lover69 on 2009-04-12
You can burn cd iso's to dvd's, I do it all the time.

---

### Post by nandemonai on 2009-04-12
Depends where you live as to what mirror but a US one for example is here:

[http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs-Ubuntu/9.04/beta/](http://mirror.mcs.anl.gov/pub/ubuntu-iso/DVDs-Ubuntu/9.04/beta/)

Mirror list here:

[http://www.ubuntu.com/getubuntu/downloadmirrors#dvd](http://www.ubuntu.com/getubuntu/downloadmirrors#dvd)

---

### Post by Paqman on 2009-04-12
You can also install off a USB stick. You can use [Unetbootin]("http://en.wikipedia.org/wiki/UNetbootin") with an existing .iso image to set that up.

---

### Post by dekerf on 2009-04-12
Oh great thanks! I wonder why they don't put these on the main ubuntu download page? Hmmm maybe cause this one's beta...

---

### Post by nandemonai on 2009-04-12
> **dekerf said:**
> Oh great thanks! I wonder why they don't put these on the main ubuntu download page? Hmmm maybe cause this one's beta...

Hit the nail on the head there ;)

---

### Post by hesjnet on 2009-04-12
if you want to use Unetbootin you have to install mtools and 7zip:

```
sudo apt-get install mtools
sudo apt-get install p7zip-full
```

---

### Post by zerhacke on 2009-04-12
If you want to, apt k3b.  It'll give you a GUI way to burn any ISO to DVD.

---

