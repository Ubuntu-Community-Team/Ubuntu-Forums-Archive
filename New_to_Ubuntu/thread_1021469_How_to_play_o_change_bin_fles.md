---
title: "How to play o change bin fles"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by theamber on 2008-12-25
Hi, I have a video file with the bin extension. Is there a way to play it or change the format without having to burn it onto a disk?
Thanks.
VCL does not play bin files but it does play a whole lot other formats.

---

### Post by taurus on 2008-12-25
MPayer plays bin file.

```
sudo apt-get update
sudo apt-get install mplayer
gmplayer filename.bin
```

---

### Post by nhasian on 2008-12-25
thats odd.  i'm pretty sure vlc does play bin files.

---

### Post by theamber on 2008-12-25
> **taurus said:**
> MPayer plays bin file.

```
sudo apt-get update
sudo apt-get install mplayer
gmplayer filename.bin
```
I can see it now but I get a message It can't find codec for audio.
I can't heard anything.

---

### Post by taurus on 2008-12-25
Click the mplayer window with the right button and go into Preferences -> Audio and pick another driver.  I use oss.  Remember, you have to restart mplayer again for the new settings to take effect.

Have you installed the ubuntu-restricted-extras?

```
sudo apt-get install ubuntu-restricted-extras
```

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by theamber on 2008-12-25
> **taurus said:**
> Click the mplayer window with the right button and go into Preferences -> Audio and pick another driver.  I use oss.  Remember, you have to restart mplayer again for the new settings to take effect.

Have you installed the ubuntu-restricted-extras?

```
sudo apt-get install ubuntu-restricted-extras
```

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I tried oss and other audio drivers but still I get the cannot find codec for audio.
I am downloading the extras.

---

### Post by theamber on 2008-12-25
I installed the extras I still can't get audio codec. Any ideas?.
I did got an error on msttcorefonts when installing the extras.

---

### Post by theamber on 2008-12-25
Totem player plays it good audio included.

---

