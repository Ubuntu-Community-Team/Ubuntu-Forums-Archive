---
title: "Conexant Audio Problems- Toshiba C655D-S5041"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by NickKourpias on 2011-03-26
I cannot get my headphones to work with Ubuntu 10.10 32-Bit. The PC is a 64-Bit system. I cannot find any drivers (That work) for my computer. Help Please!

---

### Post by wep940 on 2011-03-26
As long as you've installed 32-bit ubuntu, it won't make any difference that your system is 64-bit.
 
Please post back the output of the following:
 
lspci
 
EDIT:  
 
This will show us the PCI devices on your PC, and in particular we are looking for the line about your sound adapter.  This will help us determine what kind of driver might work.
 
I have no idea at this point - my Conextant sound in my older laptop worked as they say "out of the box", but I haven't ever tried earphones with any of my Ubuntu installations.

---

### Post by NickKourpias on 2011-03-26
> **wep940 said:**
> As long as you've installed 32-bit ubuntu, it won't make any difference that your system is 64-bit.
 
Please post back the output of the following:
 
lspci
 
EDIT:  
 
This will show us the PCI devices on your PC, and in particular we are looking for the line about your sound adapter.  This will help us determine what kind of driver might work.
 
I have no idea at this point - my Conextant sound in my older laptop worked as they say "out of the box", but I haven't ever tried earphones with any of my Ubuntu installations.

So, what should I do?

---

### Post by wep940 on 2011-03-27
[LIST]
[*]Open a terminal window - Applications/Accessories/Terminal
[*]Type:
[/LIST]lspci <press enter>
[LIST]
[*]Just copy the output and post it back here in a reply
[/LIST]

---

### Post by wep940 on 2011-03-27
Ooopppsss - sorry - I removed my text here as I thought I was posting to a different thread.

---

