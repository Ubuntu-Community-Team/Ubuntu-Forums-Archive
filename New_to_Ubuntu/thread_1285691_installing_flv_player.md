---
title: "installing flv player"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by bindu arya on 2009-10-08
how to install flv player? i am new to ubuntu..
plz help me. its urgent.

---

### Post by RichardLinx on 2009-10-08
I'm guessing you want to play a flash video file (.flv)?

You can use Totem, vlc, or MPLayer and a few others. If it didn't play for you in totem then you're probably missing the required codecs. Open a terminal and type:

```
sudo apt-get install ubuntu-restricted-extras
```

```
sudo apt-get install vlc
```
This is why I suggest new users use Linux Mint... Hope this helps.

Edit: Forgot to add:
> sudo apt-get install flashplugin-nonfree
You may or may not need that one, but it's best I suggest it anyway.

---

