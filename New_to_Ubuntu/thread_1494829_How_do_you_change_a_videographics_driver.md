---
title: "How do you change a video/graphics driver?"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by flyver on 2010-05-27
Hi,

I've been reading about the fairly common bug of splash (Plymouth) not loading during boot. (I'm actually sometimes able to see it for the last half second before the log-in screen appears.)

If I understand correctly, the problem is that I am probably not using the correct video/graphics driver. Therefore I would like to find some other drivers and install them. However I don't know how to do that.

[SIZE="2"]Graphics processor: Mobile Intel® Graphics Media Accelerator X3100
Video chipset: Mobile Intel® GM965 Express Chipset[/SIZE]

Thank you!

---

### Post by jessewilliams on 2010-05-27
Have you tried over at intellinuxgraphics.org

They are pretty good at supplying stuff that is relatively up to date. Im not too sure on the specifics of what you need myself but Im sure the guys over there will be able to help you out properly.

---

### Post by flyver on 2010-05-27
I just found out in the Ubuntu software centre that I already have an open source driver, one that should be compatible with my computer. I read somewhere that there were problems with splash when using drivers that were _not_ open source.

According to the site you recommended, "compiling and/or upgrading graphics drivers in Linux is a complex and error-prone task." Hmm, don't know if I want to try something that is unlikely to work...

Thanks for answering!

---

### Post by sandyd on 2010-05-27
try and see if adding the xorg-edgers ppa helps

---

### Post by flyver on 2010-05-27
Unfortunately no, it didn't help!

---

### Post by flyver on 2010-06-05
I never changed the drivers; I didn't need to. However regarding _why_ I wanted to change it (to make Plymouth splash work - all I had was a black screen during boot), I found a fix:

```
sudo update-alternatives --config default.plymouth
```
Then I chose the splash theme whose description differed the most compared to mine (mine was *0, I chose 2)

Then:
```
sudo update-initramfs -u
```

I did a reboot, then I did the same thing over again, only this time I chose the original splash theme.

And that's it!

Reference: [http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html)

---

