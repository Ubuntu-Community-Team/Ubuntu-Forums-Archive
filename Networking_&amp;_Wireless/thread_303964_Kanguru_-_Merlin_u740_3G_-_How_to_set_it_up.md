---
title: "Kanguru - Merlin u740 3G - How to set it up?"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by linuxmad on 2006-11-21
Hi,
I have a friend that has a wireless 3g merlin u740 from Portugal's telecom Optimus (kanguru) and we are trying to get it to work with Ubuntu edgy. Does anyone here know if it is possible? .. I have googled a bit and found out a few tutorials for the u630. This one here is very simple:
[http://linux-facil.blogspot.com/2005/11/frontend-para-ligao-kanguru-no-ubuntu.html](http://linux-facil.blogspot.com/2005/11/frontend-para-ligao-kanguru-no-ubuntu.html)
..but I guess the init strings are a bit different. 
Can anyone please help??
Thanks
José

---

### Post by linuxmad on 2006-11-21
Anyone ...Please](*,) ](*,)

---

### Post by linuxmad on 2006-11-23
I tried ... and tried... and tried.... and finally it WORKS.
I made a small tutorial which i posted in the Ubuntu Portuguese forum:
[http://ubuntu.linuxval.org/smf/index.php?topic=13455.0](http://ubuntu.linuxval.org/smf/index.php?topic=13455.0)
One of these days I will try a translation to English, but it is self explanatory.
If you guys need any help with it please contact me.


:cool:

---

### Post by Carlos Santiago on 2007-07-09
Hi,
I made a DEB package to install a wireless UMTS/3G Novatel Merlin U630 from Portugal's telecom Optimus (kanguru).
I test it on Feisty and it is working like a charm. However, if you have problems with DNS, add
```
nameserver 62.169.67.164
nameserver 62.169.67.165

```to /etc/resolv.conf

---

