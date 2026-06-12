---
title: "Video/Install problem on AOpen MiniPC"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by cacycleworks on 2009-01-19
Hey Everyone,

I'm posting more to vent than anything really. But if some poor fool is cursed with one of these cute little macmini clones, maybe this will help them.

Here's a pic of the culprit:
[IMG]http://images.anandtech.com/reviews/system/sff/aopen/minipc/thumbnails/Aopen-MiniPC-01-front.jpg[/IMG]
([here are specs if anyone is that bored]("http://usa.aopen.com/products_detail.aspx?auno=2199"))

Summary: it has intel G915 and DVI output only. The minipc ships with a DVI->VGA adapter, which apparently totally screws xorg. I tailed the error log and found a clue:
```
(EE) intel(0): Unknown EDID version 3
```
This EDID thing is where your video adapter queries the monitor for supported modes, etc. The DVI->VGA adapter kills this and leaves you with your monitor in power saving mode. Wtf?

So, I started all this with trying to install xubuntu. Twice. It boots fine, all the text interfaces are killer, but it just goes stupid on X. So I install ubuntu server and get a cli system. First thing I do is setup openssh-server ... I install a gui and it dies again -- which is when I ssh'd in and made progress.

**Why am I writing this?** Why does anyone care? This stupid little box just loves xPee. I'm so annoyed when things work better in windblows than our better world. ;)

Right now, I'm stuck ... I'm SSHd into the box from home and I can't look on the back of the monitor... Once I do that, I should be able to get the monitor specs and then I'll manually add the display lines to the xorg.conf and cross my fingers. This should work.

Good times,
:) Chris

---

