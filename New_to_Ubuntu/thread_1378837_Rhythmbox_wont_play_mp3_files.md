---
title: "Rhythmbox wont play mp3 files"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by manny43 on 2010-01-11
Hello friends

I used ripperx to convert audio CD's to MP3 format but i'm having problems with Rhythmbox cant play or burn mp3s.Could help me with this issue?Thanks
WENT ONLINE BUT COULDNT FIND ANY TUTORIALS ABOUT IT

---

### Post by Slayer. on 2010-01-11
I installed the gStreamer plugins, then restarted, and it worked for me.

---

### Post by samh785 on 2010-01-11
> **manny43 said:**
> Hello friends

I used ripperx to convert audio CD's to MP3 format but i'm having problems with Rhythmbox cant play or burn mp3s.Could help me with this issue?Thanks
WENT ONLINE BUT COULDNT FIND ANY TUTORIALS ABOUT IT
have you installed all of the restricted formats for ubuntu?

go here if you don't know what I'm talking about: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by running_rabbit07 on 2010-01-11
Have you installed ubuntu-restricted-extras? You can find the package in Synaptic Package Manager or via terminal with,```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by k64 on 2010-01-11
My suggestion:

```
sudo apt-get install vlc
```

This will install the VLC media player, which can play such files without the need for those proprietary codecs.

---

### Post by manny43 on 2010-01-12
> **running_rabbit07 said:**
> Have you installed ubuntu-restricted-extras? You can find the package in Synaptic Package Manager or via terminal with,```
sudo apt-get install ubuntu-restricted-extras
```
sudo apt-get install ubuntu-restricted-extras

---

### Post by running_rabbit07 on 2010-01-12
> **manny43 said:**
> sudo apt-get install ubuntu-restricted-extras
Did that work for you? If so, please mark as solved.:D

---

