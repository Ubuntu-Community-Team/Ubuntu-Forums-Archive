---
title: "rtl8180 &amp; ndiswrapper not working"
date: 2005-03-25
forum: Networking &amp; Wireless
---

### Post by andygodwin on 2005-03-25
I'm trying to get an Edimax 7106-PC Wireless card (this has a rtl8180 chipset in it) to work under Ubuntu. This is a fresh install, and I can get ndiswrapper to accept the drivers and load as a module, at which point the Tx/Rx light starts blinking. However, I can't get iwconfig to set the mode or essid, yet it will accept a WEP key.

I've had the card working before, with ndiswrapper 0.7 and kernel 2.6.9. However, it seems that Ubuntu uses the 2.6.10 kernel, and I can't compile 0.7 under it (I have tried).

Any suggestions? It is something I'm doing wrong in trying to initiaise the card, or is it an incompatability?

---

### Post by andygodwin on 2005-03-26
Don't worry, all solved. A reboot followed by using the right key (this had me for a while, I had to force it to 128bit encryption) solved it. Just have to use the gnome network properties applet and that was it.

---

### Post by mehaga on 2005-04-13
I have the same problem and haven't fixed it yet. What exactly did you do to make it work?

Thaks in advance.

---

### Post by mehaga on 2005-04-14
:)

It works :)

I found the solution elswhere in the forums:
'iwconfig wlan0 key open'
that's all it took :)

---

