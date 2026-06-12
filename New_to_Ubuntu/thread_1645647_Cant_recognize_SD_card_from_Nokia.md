---
title: "Cant recognize SD card from Nokia"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by wordstar on 2010-12-14
Hello,

I am using Ubuntu 8.10 and windows XP.  Generally, I consider ubuntu superior to Windows in dealing with different formats of partitions because it can see other kinds of partitions which windows cannot see.

A few weeks ago, i needed to copy a picture taken from my nokia phone 2730c1 to my computer.  After putting the phone's micro SD card into my computer, windows XP complained that the card was not formatted.  i tried it on Ubuntu 8.10 which was able to recognize the size of the card (1gb) but complained that it didnt have a suitable partition table.

I tried to figure out what kind of partition Nokia was using on their phones but couldnt find it on the net.  Anyway, when I tried the card on a computer running Windows 7, it worked great!

i am surprised that Windows 7 was able to recognize a type of partition which my ubuntu wasnt able to recognize.  My questions:

What type of partition did my Nokia phone use?
Can the latest ubuntu recognize this partition?
Will my Ubuntu 8.10 still be useful if I upgrade it with something to recognize this partition?

Thanks aplenty!

---

### Post by Foxheadz on 2010-12-14
If you right click on it and say properties does it say the format? and if you look at it in gparted what does it say?

---

### Post by owiknowi on 2010-12-14
some thoughts:
1. are the files perhaps hidden?
if so make them visible by choosing View/Show hidden files in file manager.
2. install nokia drivers (if available for you version).
3. workarounds: 
- connect phone through bluetooth with your pc and send file(s).
- connect through a usb cable in case your phone has this option

it's possible however that a newer version of ubuntu does recognize the card.
you can try this by downloading a live cd of ubuntu 10.

---

