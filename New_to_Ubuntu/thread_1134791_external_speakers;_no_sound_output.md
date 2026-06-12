---
title: "external speakers; no sound output"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by Saint_ on 2009-04-23
Alright, I recently installed kubuntu (roughly 4 days ago) and I've been sorting out drivers, etc. So as such, I've come across another lol. When i plug in my external speakers, no sound comes through 'em, but i can tell they're on due to the faint static and "on" sound they put off (sound works fine through my laptops speakers though). 

The speakers are: [http://accessories.us.dell.com/sna/products/Video_Conferencing/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=313-4025](http://accessories.us.dell.com/sna/products/Video_Conferencing/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=313-4025)

I've tried changing the master channel via system > sound but none of the options seemed to work. So I don't know if im missing some type of driver or what but this is what i've come up with so far.

saint@saint:~$ lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

Thanks in advance for any and all help.

---

### Post by duanedesign on 2009-04-23
In terminal type

```
alsamixer
```

and make sure all your levels are turned up. Some people have been having trouble with the PCM level defaulting to 0.

If that does not work here is a good guide:
[http://ubuntuforums.org/showthread.php?t=789578&highlight=alsamixer](http://ubuntuforums.org/showthread.php?t=789578&highlight=alsamixer)


Good luck

EDIT: some people have noticed the following:
- Set PCM to 80% and Master to 100%. Sound is OK
- Set PCM to 100% and Master to 80%. Sound is distorted.

---

### Post by Saint_ on 2009-04-23
Alright, thanks for the quick reply. My PCM was defaulted at 76 though, so I don't think that's the problem.

---

### Post by Saint_ on 2009-04-24
anybody?

Edit: missed that URL guide link, checking into it now. - whoot it worked, thanks.

---

