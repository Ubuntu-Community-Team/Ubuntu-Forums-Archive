---
title: "Gimp save issue with Karmic"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2010-02-18
Since upgrading to Karmic Koala, I've had a serious problem with Gimp. In Jaunty, Gimp would always have the list of save options that would allow me to save a gimp project as  a Jpeg or anything else. Now, Gimp only gives me 4 save options, all gimp related so I can't even upload the pictures to the internet or even view them on a computer without gimp. I've checked the drop-down list with the save options and their not there. I've tried uninstalling it and reinstalling it. Even more strange, I've had to reinstall Karmic several times (my own stupidity) and once Gimp HAD the save options, but now it doesn't. Is there anyway to get those save options?

---

### Post by bodhi.zazen on 2010-02-18
When saving a file -> Save as -> Select File_Type (By Extension)

In that menu I have all the various options.

---

### Post by Captainflowers91 on 2010-02-18
yea, I know that, but on that menu, the only options I have are:

Gimp XCF image

bzip archive

gzip archive.

I have no idea how to get the other options

---

### Post by bodhi.zazen on 2010-02-18
How did you install Karmic ? Is this a minimal install you then built up ?

If so, you are going to start installing libpng12-0 and what not.

---

### Post by Captainflowers91 on 2010-02-19
I thought I did the full install from the disk I downloaded the ISO for from Ubuntu.com.

---

### Post by Captainflowers91 on 2010-02-20
Nope, no luck. Is there a way to completely remove all traces of Gimp and then reinstall from the beginning?

---

### Post by bodhi.zazen on 2010-02-21
You can remove and re-install gimp if you wish.

On the command line, use the purge option with apt-get

```
sudo apt-get purge gimp
sudo apt-get install gimp
```

---

