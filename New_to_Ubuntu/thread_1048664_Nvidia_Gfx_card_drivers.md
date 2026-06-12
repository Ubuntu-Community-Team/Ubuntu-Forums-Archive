---
title: "Nvidia Gfx card drivers"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by mac9416 on 2009-01-23
I plan on getting this card:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814133239](http://www.newegg.com/Product/Product.aspx?Item=N82E16814133239)
and I want to have proprietary drivers for it when it arrives. My 7.10 box is not connected to the net, so apt-get ain't an option. Remember, I'm running 7.10.
Thanks!

---

### Post by taurus on 2009-01-23
If your computer is not connected to the net to install a driver for it, you just have to download the .run for Linux from nvidia's site.  Then, install it by hand from a terminal.

---

### Post by Michael.Godawski on 2009-01-23
Just as a side note:

once downloaded you install the drivers with

```
sh NVIDIA-Linux-x86-180.22-pkg1.run
```

---

### Post by taurus on 2009-01-23
> **Michael.Godawski said:**
> Just as a side note:

once downloaded you install the drivers with

```
sh NVIDIA-Linux-x86-180.22-pkg1.run
```

Probably needs the _sudo_ in front too.

---

### Post by mac9416 on 2009-01-23
Thanks, man.
Can anyone confirm for me that this is the one?:
[http://www.nvidia.com/object/linux_display_ia32_180.22.html](http://www.nvidia.com/object/linux_display_ia32_180.22.html)

Thanks!

---

### Post by Michael.Godawski on 2009-01-23
If you are running 32- bit it should be this one.

About the sudo in front of the sh command... I thought that too, but the nvidia sites does not say this. Don't they know better or is the sudo redundant in this case?

---

### Post by mac9416 on 2009-01-23
Alright, guys, that makes me a very happy person. Thanks!

---

### Post by taurus on 2009-01-23
> **Michael.Godawski said:**
> 
About the sudo in front of the sh command... I thought that too, but the nvidia sites does not say this. Don't they know better or is the sudo redundant in this case?

They are assuming you've logged in as root.  Therefore, you just run it the way they have it on their website.  And we all know about root account on Ubuntu.  Also, they assume you don't have X server running so you need to shut down gdm before you can install nvidia driver for your graphic card.  Otherwise, nvidia installer will complain about it.

---

### Post by Michael.Godawski on 2009-01-23
> **taurus said:**
> They are assuming you've logged in as root.  Therefore, you just run it the way they have it on their website.  And we all know about root account on Ubuntu.  Also, they assume you don't have X server running so you need to shut down gdm before you can install nvidia driver for your graphic card.  Otherwise, nvidia installer will complain about it.

Thank you for the clarification Taurus. :P

---

