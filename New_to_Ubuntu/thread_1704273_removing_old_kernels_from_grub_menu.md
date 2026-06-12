---
title: "removing old kernels from grub menu"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by tushar maroo on 2011-03-10
i have a dell studio laptop,and i have dual installation of ubuntu lucid +windows 7.
by updates now i have 4 kernels of ubuntu........so how can i remove them from the grub menu???

---

### Post by oldos2er on 2011-03-10
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

---

### Post by bodhi.zazen on 2011-03-10
Personally I would remove them rather then hide them.

---

### Post by ssulaco on 2011-03-10
> **tushar maroo said:**
> ........so how can i remove them from the grub menu???

> **bodhi.zazen said:**
> Personally I would remove them rather then hide them.

I would to........
I dont know what kernel you are running....Take mine for example  2.6.24-28-generic ,I only keep 2,incase one goes haywire, I can still boot off the old one.so say I have 25,26,27,28,and I want to get rid of 25 and 26
Iwould run
```
sudo apt-get remove --purge 2.6.24-25-*
```
when finished run
```
sudo apt-get remove --purge 2.6.24-26-*
```
linux images and headers can take up considerable HDD space,especially if you have a bunch of old kernels.

---

### Post by bodhi.zazen on 2011-03-10
"considerable" hd space is relative to the size of the HD, LOL.

An "easy" way to remove old kernels is with Synaptic. I keep the current + 1 old.

To see your current kernel, use uname .

---

### Post by wormyblackburny on 2011-03-10
once you remove them, dont forget to do sudo update-grub to update the list.

+1 on using synaptic to remove them, keeping 1 spare kernel.

You could also install Ubuntu Tweak from the software center, love that program.

---

### Post by barney385 on 2011-03-10
I just go into Synaptic and remove them.

I always leave 3 kernels in grub just in case I start experimenting and bork my set up.

Just remove the Generic Linux Images you don't need the Synaptic way.

---

### Post by ssulaco on 2011-03-10
> **bodhi.zazen said:**
> "considerable" hd space is relative to the size of the HD, LOL.

I had picked up a new seagate 30g drive off ebay for 12 bucks,so yes for me HD space is valuable;)

---

### Post by philinux on 2011-03-10
> **tushar maroo said:**
> i have a dell studio laptop,and i have dual installation of ubuntu lucid +windows 7.
by updates now i have 4 kernels of ubuntu........so how can i remove them from the grub menu???

Easy way with a one line command. Link in first paragraph. Scroll down to see the dry run version and then the do it for real command. Just a copy and paste into a terminal.

[http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/](http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/)

---

### Post by ssulaco on 2011-03-10
> **philinux said:**
> Easy way with a one line command. Link in first paragraph. Scroll down to see the dry run version and then the do it for real command. Just a copy and paste into a terminal.

[http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/](http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/)

> **ssulaco said:**
> 
```
sudo apt-get remove --purge 2.6.24-25-*
```

The wildcard will grab everything associated with the kernel...images,headers and restricted-modules for the kernel your purging.

---

### Post by domu on 2011-03-11
I have a script 'remove-kernel' which shows all installed kernels and can remove ones you don't want, you can get it from 'My Programs' at [http://www.timedicer.co.uk](http://www.timedicer.co.uk)

HTH

---

### Post by amalnath on 2011-03-11
is it alright to remove old kernels using application-***"gtkorphan"(remove orphaned packages)***  ??:-k

---

