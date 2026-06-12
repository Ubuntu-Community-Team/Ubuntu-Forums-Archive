---
title: "cant intstall flashplayer"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by nj96 on 2009-04-21
I cannot watch videos on my Ubuntu 8.10; when i download the adobeflash player for ubuntu 8.04+ .deb, and when the package installer comes up; it says Error: wrong architecture 'i386'

---

### Post by llamabr on 2009-04-21
Don't download the deb, use apt:

flashplugin-nonfree - Adobe Flash Player plugin installer

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by tarps87 on 2009-04-21
> **nj96 said:**
> I cannot watch videos on my Ubuntu 8.10; when i download the adobeflash player for ubuntu 8.04+ .deb, and when the package installer comes up; it says Error: wrong architecture 'i386'

What version of Ubuntu are you using, 64bit or 32bit?

Why don't you install it from the repository
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by 3rdalbum on 2009-04-21
If i386 is the wrong architecture, then you're running 64-bit.

I suggest downloading the 64-bit version of Flash Player from the Adobe website; I don't think Ubuntu has the 64-bit Flash Player packaged yet, only the 32-bit player with a special wrapper that doesn't always work.

---

### Post by tarps87 on 2009-04-21
> **3rdalbum said:**
> If i386 is the wrong architecture, then you're running 64-bit.

I suggest downloading the 64-bit version of Flash Player from the Adobe website; I don't think Ubuntu has the 64-bit Flash Player packaged yet, only the 32-bit player with a special wrapper that doesn't always work.

I can never remember if the error message says the yours or the one it expects #-o

The command above will sort it for you. I'm currently using flash player on a 64bit machine and haven't notices any problems so far

---

### Post by nandemonai on 2009-04-21
Installing restricted extras helps sort out these issues.

I'd suggest reading [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) before installing it though.

---

### Post by gandaran on 2009-04-21
install 64-bits adobe flash, remove all flash installed and follow this [guide]("http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml")

---

### Post by oldos2er on 2009-04-21
> **nj96 said:**
> I cannot watch videos on my Ubuntu 8.10; when i download the adobeflash player for ubuntu 8.04+ .deb, and when the package installer comes up; it says Error: wrong architecture 'i386'

 64-bit Flash is here: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

---

