---
title: "Ubuntu Maverick Booting Into Shell Automatically"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by 1n73rn37_j3d1 on 2010-10-21
Hey there, everyone, this is my first time posting on the Ubuntu forums. Yay me!

Anyhow, I have a quick question. I've been using Ubuntu Maverick for a couple weeks now and I really like it. I've always used one form of Windows or another, and I'm happy to say that I've been converted!

As a reward for my good deeds, however... Sometimes Ubuntu simply boots into a shell environment without me explicitly telling it to boot into one. Normally from there I just do another reboot, and I get my normal GNOME desktop back, but this is rather annoying to do. Any tips or advice on how to stop this occurrence from happening? While I'm learning slowly how to use the CLI more and more... I'm not ready to use it all the time! :P

Thanks a ton for any help!

---

### Post by LowSky on 2010-10-21
Welcome to the Forums and to Ubuntu

if it boots into the consol dont reboot, just sign in and type ```
startx 
```and it will go into the GUI..

It shouldnt boot to consol unless you wish it to.
Could you tell us how you install Ubuntu, did you use WUBI?
What type of video card are you using? Any pieces of equiptment like a printer or PCI card you may have that isn't running correctly could also keep the GUI form starting.

Anything you think may be an issue please feel free to tell us.

---

### Post by 12apennachi on 2010-10-21
On startup, if you get a black screen that says login: type in your login name, the passowrd, once you get there type in this:

```
sudo start gdm
```

---

### Post by 1n73rn37_j3d1 on 2010-10-22
> **LowSky said:**
> Welcome to the Forums and to Ubuntu

if it boots into the consol dont reboot, just sign in and type ```
startx 
```and it will go into the GUI..

It shouldnt boot to consol unless you wish it to.
Could you tell us how you install Ubuntu, did you use WUBI?
What type of video card are you using? Any pieces of equiptment like a printer or PCI card you may have that isn't running correctly could also keep the GUI form starting.

Anything you think may be an issue please feel free to tell us.

I couldn't tell you the exact model of graphics card, but I think it's an nVidia GeForce 9200 with 1GB memory. I don't have a printer attached to my laptop, and I certainly hope it's not the PCI card that's busted!

I also installed Maverick from a fresh install, the final version. I wiped my hard drive first, so it really was a fresh install. Hope this helps some!

---

