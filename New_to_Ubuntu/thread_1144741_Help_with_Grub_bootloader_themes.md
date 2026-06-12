---
title: "Help with Grub bootloader themes"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by ives31 on 2009-05-01
Hi,
I installed the startup manager and I noticed that there was options to install a Grub bootloader.
I tried to tick the box but it wouldn't tick. I did a little research and found that I needed to install something called gfxboot. I installed that via synaptic but I still can't tick the box in startup manager and get any bootloader themes to work.
Does anyone have any help for a noob?

cheers,
Ives

PS I'm running 9.04

---

### Post by Didius Falco on 2009-05-01
Here is a great guide to doing Grub bootloader splashimages:

[http://users.bigpond.net.au/hermanzone/p15.htm#splash](http://users.bigpond.net.au/hermanzone/p15.htm#splash)

There is a lot more great info about the Grub bootloader there - I highly recommend bookmarking this site for further study and use.

I hope this helps...

---

### Post by ives31 on 2009-05-01
I'm a bit confused.
Are splash screens the same as themes for Grub?

---

### Post by Niniel on 2009-05-01
Sort of.
There aren't any "themes" for Grub as such, although you can set a different background image, and you can also change the colours of of the text and of the selection bar.
KGrubEditor is great for setting - and making! - background images for Grub, although I don't think it can handle the colours.
For that, you'll have to manually add to your menu.lst file
```
foreground ffe4b5
background f4a460 
```
Changing the alphanumeric codes will give you different colours.

---

