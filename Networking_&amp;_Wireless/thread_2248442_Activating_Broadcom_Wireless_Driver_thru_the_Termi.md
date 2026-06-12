---
title: "Activating Broadcom Wireless Driver thru the Terminal"
date: 2014-10-14
forum: Networking &amp; Wireless
---

### Post by rodel_catajay on 2014-10-14
I tried activating the Broadcom wireless driver for an ACER Aspire One Netbook, it didnt work out using the UI, is there a command line to this using the Terminal?

thanks.

---

### Post by mörgæs on 2014-10-14
Moved your thread to Networking. Please read the sticky notes.

---

### Post by Hadaka on 2014-10-14
Hi, please open a terminal ctrl/alt/t then
COPY and paste these commands one at a time..
```
lspci -nn | egrep '0200|0280'
rfkill list all
lsmod | egrep 'wl|b43|brcmsmac'
uname -r
```
post the output and please use code tags
thanks

---

### Post by Bucky Ball on 2014-10-14
Please give a lot more detail on what you've done so far. Couldn't get it working through the UI? What UI and what did you do to activate it? Has it ever worked? What Broadcom card is it? There are many.

Please open a terminal and post back the output of these two commands:

```
sudo lshw -C network
iwconfig
```

* Ninja-ed by Hadaka. ;)

Post the output of their commands, please.

---

### Post by rodel_catajay on 2014-10-15
thanks I will try this one when I got home.

---

### Post by rodel_catajay on 2014-10-15
thanks, still striving to learn more, techniques in running Linux.

---

