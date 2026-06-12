---
title: "can't watch cnn"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by shadowlands on 2009-01-03
videos or mega video.  Can someone please help me with this?

---

### Post by Helios1276 on 2009-01-03
have you got your codecs ?

---

### Post by shadowlands on 2009-01-03
.Thanks for responding to me. I do not think so. How do I check to  see if I have them and if now do I obtain the codecs?  > **Helios1276 said:**
> have you got your codecs ?

---

### Post by taurus on 2009-01-03
Probably the ubuntu-restricted-extras package.

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by shadowlands on 2009-01-03
The video now appears instead of a blank space but they will not load up and play. Anny suggestions?> **taurus said:**
> Probably the ubuntu-restricted-extras package.

```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Helios1276 on 2009-01-03
Have a go at this,

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Helios1276 on 2009-01-03
Also, for videos I would recommend VLC player if you haven't already got it.

---

### Post by sofasurfer on 2009-01-03
This solved all my video problems. Comprehensive Multimedia & Video Howto [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by freebyte on 2009-01-03
Try this
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

---

### Post by Helios1276 on 2009-01-03
> **sofasurfer said:**
> This solved all my video problems. Comprehensive Multimedia & Video Howto [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Nice work man. medibuntu is the way to go

---

### Post by shadowlands on 2009-01-03
got this one.  I can view live video from CNN but I can not view the video archive.  I see the still but, that is, because thevideo will not load to play.
> **freebyte said:**
> Try this
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

---

### Post by shadowlands on 2009-01-03
used it.  I think I used the 
"gksudo gedit /etc/mplayerplug-in.conf" incorrectly.  Do you erase what is on the page that pops up an past in the stuff or was it to be added on to what was already on that page?:popcorn:> **sofasurfer said:**
> This solved all my video problems. Comprehensive Multimedia & Video Howto [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by sofasurfer on 2009-01-03
I had a similar problem recently with [www.clickondetroit.com](www.clickondetroit.com) (WDIV) where I could see some videos but when I clicked on other links the browser would close. I was told it was a website issue. A couple days later it started working properly.

---

### Post by shadowlands on 2009-01-03
Nothing closes the video just will not load and play.It read loading but nothing ever loads up to play.> **sofasurfer said:**
> I had a similar problem recently with [www.clickondetroit.com](www.clickondetroit.com) (WDIV) where I could see some videos but when I clicked on other links the browser would close. I was told it was a website issue. A couple days later it started working properly.

---

