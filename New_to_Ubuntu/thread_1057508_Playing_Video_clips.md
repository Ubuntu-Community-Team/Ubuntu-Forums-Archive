---
title: "Playing Video clips"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by sai224 on 2009-02-01
Hi,
I run a Dual boot on Asus A6000KM laptop with Ubuntu and Windows XP. I have 2 X T/Bird accounts (same email address) 1 on Ubuntu and other on XP. When I receive video clip on T/Bird on WinXP I can easily play in on WinXP with VLC player,but when I receive same clip on Ubuntu T/Bird and try to play with Totem it goes half way and stops with error message saying 'streaming error',I have also loaded VLC from Ubuntu repositories, but this does not appear on 'drop box' when asked whether I wish to play on Totem, any help gratefully accepted..thanks in advance.

---

### Post by Crafty Kisses on 2009-02-01
Do you have all the codecs installed?
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Zevik on 2009-02-01
The best way to ensure all proper codecs for DVDs and Windows Media and other various formats are installed is to enable everything Medibuntu has to offer, check [THIS]("http://gn00buntu.blogspot.com/2008/12/medibuntu-movies-mp3-playback.html") out for detailed instructions.

---

### Post by sai224 on 2009-02-02
> **Codename said:**
> Do you have all the codecs installed?
```
sudo apt-get install ubuntu-restricted-extras
```
Hi, Am not sure am very new to this, but will try as you suggest.Thanks

---

### Post by Crafty Kisses on 2009-02-02
After you run that command you should be set, if you have any problems please post back.

---

### Post by leonardo_neo on 2009-02-02
Also probably you would like to install medibuntu repository and codecs

Here is the link

> [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

You need to install

**libdvdcss2** and **w32codecs**

Try it, and you are ready for most of the media formats. :)

---

### Post by sai224 on 2009-02-02
> **leonardo_neo said:**
> Also probably you would like to install medibuntu repository and codecs

Here is the link



You need to install

**libdvdcss2** and **w32codecs**

Try it, and you are ready for most of the media formats. :)
I am very new to this, but I will try, is that the good old Indian flag I see, was born there myself!! Thanks

---

