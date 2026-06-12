---
title: "Fresh install of Lubuntu 12.04 and Wireless does not work"
date: 2013-10-30
forum: Networking &amp; Wireless
---

### Post by sdep777 on 2013-10-30
Fresh install of Lubuntu 12.04 and Wireless does not work ....help

I have a fresh install of Lubuntu 12.04 ( I like it ) and everything works fine but NO wireless and my laptop has wireless built in.

What do I need to download from Synaptic Pkg manager to get this to work properly. ? 


Equipment used

Dell laptop 
500 GB drive fresh install Lubuntu 12.04
Wireless card
runs great .


Thank You,
Steven

---

### Post by Hadaka on 2013-10-30
Hi,please open a terminal..ctrl/alt/t and enter..
```
lspci -nnk | grep -iA3 net
rfkill list all
lsmod
```
post the output
thanks.

---

### Post by mörgæs on 2013-10-30
12.04 is out of support. You will be better off with a fresh install of 13.10.

---

### Post by sdep777 on 2013-10-30
Thank you !

---

### Post by Hadaka on 2013-10-30
How long have i been sleeping? Morages..did you mean 10.04?
12.04 is good till 2017...and i believe 13.10 expires before 12.04
sooo. If you want to use the 12.04LTS we can continue...or you can
load 13.10...let us know.
thanks

---

### Post by mörgæs on 2013-10-30
Ubuntu 12.04 is long term support, but not Lubuntu. The latter is already out of juice.

---

### Post by mörgæs on 2013-10-30
I see you have opened a new thread. If you don't need more answers here please mark this one 'solved' using 'thread tools'.

---

