---
title: "Wireless PCMCIA w/certified drivers"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by memnauk on 2007-07-03
Hey all,

First time poster.  I have been fighting with several different wireless PCMCIA cards and the ndiswrapper.

I was wondering if there are any cards on the market that are out of the box with Linux drivers included?

I am running Ubuntu Feisty atm and really want to get it online via my WAP.

Thanks
Memnauk

---

### Post by zach12 on 2007-07-03
yes my asus wifi card (Linux drivers included) works out of the box

---

### Post by fredj on 2007-07-04
How did you install ndiswrapper. There is a horrible bug in the version of ndiswrapper distributed
with Feisty, it just doesn't work. 
Open a terminal window and type in 'ndiswrapper -v' to get your version of ndiswrapper then
post the message that is returned in full. Most people end up having to compile the latest version
of ndiswrapper from the source files to get it to work correctly.

---

