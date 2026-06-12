---
title: "Madwifi issue"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by 2j4ez on 2008-09-10
Hello I wonder is some one can help

I had a to format my ubuntu box and start from scratch now my wireless is not working

lspci says i got a atheros 242x wireless card

I downloaded the madwifi driver from the website and from a snapshot

I started terminal and went to the madwifi directory and typed

make
sudo make install

It seemed to install but still does not work.
When i install another driver it says WARNING:
It seems that there are modules left from previous MadWifi installations.
If you are unistalling the MadWifi modules please press "r" to remove them.
If you are installing new MadWifi modules, you should consider removing those
already installed, or else you may experience problems during operation.
Remove old modules?

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ? 
Pressing R does not seem to remove them the same message appears when i goto install another driver

 
Found a how-to on ubuntu geek but following there instructions only seems to download a readme file

Any ideas anybody please help ive formated this laptop 5times to night trying ti get it to work!

---

### Post by 2j4ez on 2008-09-11
I will blame my brother he has turned my wireless switch off just switched it back on and tried ndiswrapper and a inf file it works got wireless now

---

