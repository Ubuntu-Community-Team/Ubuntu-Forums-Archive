---
title: "screen flicker"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by goldenfleece on 2009-01-11
Problem:  Screen flicker - seems worse after install...

Basic Hardware and other info: new ubuntu user, new install on intel desktop XBX2 board/ATI graphics card/ Princeton widescreen LCD with DVI connection

Done so far: I tried several resolution options, no luck.  

Any suggestions?

---

### Post by Drubie on 2009-01-11
Are you using a free (as in free speech) video driver or a proprietary one?  also, which one?

---

### Post by goldenfleece on 2009-01-12
I just discovered that most ATI graphics cards are not open.
However, I partially solved the problem by switching my bios to a PCIe enabled.  I still get flicker but not nearly as much as when bios graphics setting was PCI.

I think I have a card (will fill in when I can) by ATI.  
I may have to search for another Graphics card and save this ATI card for a windows machine.

Suggestions for a good open card?

---

### Post by TheLions on 2009-01-12
Nvidia is producing GeForce and ATI Radeon!
:lolflag:

which one do you have?

---

### Post by goldenfleece on 2009-01-12
yeah, brain got stuck.
I have an ATI x1950Pro w/ 256MB.

---

### Post by TheLions on 2009-01-13
if i were you i would try installing new drivers eather from ati webpage:
[http://ati.amd.com/support/driver.HTML](http://ati.amd.com/support/driver.HTML) or with envy:
```
sudo apt-get install envy
```

---

### Post by goldenfleece on 2009-01-14
Perfect.  Thanks.

---

