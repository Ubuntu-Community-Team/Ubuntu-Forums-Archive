---
title: "If I apply this code - can I play DVD's?"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by listerdl on 2009-02-21
Hi All

If I enter this code into terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

Will/should I be able to play DVD's?

---

### Post by sandyd on 2009-02-21
no

```

sudo apt-get install libdvdcss


```

add that in and ill play dvds

---

### Post by binbash on 2009-02-21
you need libdvdcss2 (add medibuntu to your repos then sudo apt-get update && sudo apt-get install libdvdcss2)

---

### Post by theozzlives on 2009-02-21
Not encrypted ones after the restricted extras, you want to enter:
```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential   debhelper fakeroot
```
then:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
Select Movie Player (xine) when you play them.

---

### Post by theozzlives on 2009-02-21
> **binbash said:**
> you need libdvdcss2 (add medibuntu to your repos then sudo apt-get update && sudo apt-get install libdvdcss2)

libdvdread3 has libdvdcss2 with it.

---

### Post by listerdl on 2009-03-09
I did all the above and I can play DVD's - so thanks!

But....something very strange happened...half way through watching a movie it asked me to confirm that I have installed libdvdcss?

Did I not install the software correctly?

---

### Post by gandaran on 2009-03-09
> **listerdl said:**
> I did all the above and I can play DVD's - so thanks!

But....something very strange happened...half way through watching a movie it asked me to confirm that I have installed libdvdcss?

Did I not install the software correctly?
open synaptic and check if it's installed!
if you did run this code
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
then you have an older version of libdvdcss installed, install the one from the medibuntu repository.

---

### Post by theozzlives on 2009-03-09
> **gandaran said:**
> open synaptic and check if it's installed!
if you did run this code
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
then you have an older version of libdvdcss installed, install the one from the medibuntu repository.

The code I gave works on my 8.10 machines. I watch Girls Gone Wild all the time hehe.

---

### Post by gandaran on 2009-03-09
> **theozzlives said:**
> The code I gave works on my 8.10 machines. I watch Girls Gone Wild all the time hehe.
yes it works, but libdvdcss2 from the medibuntu is more recent/update

---

### Post by mc4man on 2009-03-09
the "/usr/share/doc/libdvdread3/install-css.sh" in 8.10 and probably also 9.04 has been rewritten to retrieve from medibuntu and is current.

---

