---
title: "Winbond w6692cf LAN card"
date: 2014-06-18
forum: Networking &amp; Wireless
---

### Post by No_ on 2014-06-18
I Got winbond w6692cf LAN card.  How to connect to net and how i check Mac adres of card?  I Got lubuntu and is is Old comp help me pls

---

### Post by chili555 on 2014-06-18
To connect to the net, you may need a driver. First, let's identify the card. Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn | grep 0200
ifconfig
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by mörgæs on 2014-06-18
Are you sure it's a LAN and not an ISDN card?

---

### Post by chili555 on 2014-06-18
> **mörgæs said:**
> Are you sure it's a LAN and not an ISDN card?No, actually! How do we identify the card/drivers?

I love and hate very old and very new devices!

@No_  Please instead post:```
lspci -nn
```

---

### Post by No_ on 2014-06-19
Got something like that so what to do next? 
[http://s18.postimg.org/4x9cxkmuh/IMAG0149.jpg](http://s18.postimg.org/4x9cxkmuh/IMAG0149.jpg)

---

### Post by chili555 on 2014-06-19
Your device should be claimed by the rare driver *hisax*:```
$ modinfo hisax | grep 1702
alias:          pci:v0000[COLOR="#FF0000"]0675[/COLOR]d0000[COLOR="#FF0000"]1702[/COLOR]sv*sd*bc*sc*i*
```See if the driver loaded automatically:```
lsmod | grep hisax
```Searching the web, I saw this: [http://manpages.ubuntu.com/manpages/trusty/man8/hisaxctrl.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/hisaxctrl.8.html)

Frankly, this is my only exposure to such matters and I can offer no other suggestions.

---

