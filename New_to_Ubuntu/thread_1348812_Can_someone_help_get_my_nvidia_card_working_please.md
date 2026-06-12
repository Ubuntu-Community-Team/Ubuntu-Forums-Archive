---
title: "Can someone help get my nvidia card working please"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by guy72277 on 2009-12-07
Hi, I have an nvidia geforce 4000 mx card and have tried a few things but cannot get it working.  I have installed the recommended driver, but the nvidia x server says "you do not appear to be using the nvidia x driver.  Anyone able to help me out.

Thanks

Guy

---

### Post by falconindy on 2009-12-07
Which driver did you install? You should be using the 96 series driver.

---

### Post by guy72277 on 2009-12-07
Yep, that's the one I'm using....

---

### Post by falconindy on 2009-12-07
You may need an xorg.conf file for X to find the drivers, then. In a terminal, do this:

```
sudo nvidia-xconfig
```

That should generate a file at /etc/X11/xorg.conf.

---

### Post by guy72277 on 2009-12-07
Hi,

have done that, restarted and get "the flickering login screen", from which I can choose to run ubuntu in low graphics mode ( this is a new development, as it just flickered a couple of weeks ago)  then I'm back with the same message from the nvidia card as before - you do not appear to be using the Nvidia X driver, please edit your x configuration file (just run 'nvidia-xconfig' as root and restart the x server.

BTW, thanks for replying on this, I really hope to get it sorted this evening......


Guy

---

### Post by Stubbs3 on 2010-01-19
I'm having the same exact issue with my 8600gt and Ubuntu 9.1 

Did you resolve your problem?

I'm new to Ubuntu but have looked into and i have tried a couple of things. The only thing that seems to work so far for me is to remove all restricted drivers. 

The only downfall I've noticed is i cant run enhanced desktop visual effects and some video playback is choppy/lags.

If you have any more information to help me would be greatly appreciated.

Thanks, Ryan

---

### Post by sandyd on 2010-01-19
i believe you need to use the drivers from the nividia site for that as that card is really old.

---

### Post by SirBismuth on 2010-01-20
I have a 7600GT, and use the drivers from the NVIDIA site.  Of course, almost every time there is a kernel update, I have to reinstall the drivers.  Not a big deal, I can almost do the entire process, including shutting gdm if necessary, with my eyes closed.

B

---

