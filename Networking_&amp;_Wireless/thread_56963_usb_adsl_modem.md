---
title: "usb adsl modem?"
date: 2005-08-14
forum: Networking &amp; Wireless
---

### Post by british_government on 2005-08-14
just wondered if it was posisble to use this with my full install of ubuntu because its my only access to the internet
and if anyone knows how advice would be appreciated
thanks

---

### Post by OwlManAtt on 2005-08-14
A USB ADSL modem, eh? Can you be more specific? Is it the 2Wire? Last I checked (RedHat nine days, mind you, but I don't think much has changed for the 2Wire since back then), you could not connect to the 2Wire via USB from Linux with any sort of native driver written for Linux.

However, you might want to give ndiswrapper a try on the 2Wire USB drivers for Windows. I don't know if you'll have any success, but it's worth a shot.

---

### Post by british_government on 2005-08-14
yeah 2 wire sagem fast ok thanks for that tried the load disks and loads downloads thanks anyways

dont suppose you know any possible way around this except a router and ethernet card do u?

---

### Post by OwlManAtt on 2005-08-14
[QUOTE=british_government]yeah 2 wire sagem fast ok thanks for that tried the load disks and loads downloads thanks anyways

dont suppose you know any possible way around this except a router and ethernet card do u?[/QUOTE]
 Your 2Wire has an RJ-45 port (the thing you plug your Cat5 into), does it not? All you'd need it an ethernet card to connect to it.

But before you go and buy an ethernet card, give ndiswrapper a shot. It creates a kernel module that wraps a Windows driver, such as the 2Wire USB driver. Have a look at the [wiki page](https://wiki.ubuntu.com/HowToSetUpNdiswrapper) for more information on setting this up.

---

### Post by british_government on 2005-08-14
it has one rj 45 port which connects to the telephone line and a usb which connect to the usb, surely i would need a router for it to work with an ethernet because you cant plug a dsl line straight into an ethernet port can you?

---

### Post by OwlManAtt on 2005-08-14
Are you sure that it doesn't have both a port for telephone cable to connect it to the wall jack *and* a port to plug some cat5 in to? My model did.

If not, and you cannot get the driver to work with ndiswrapper, you'll have to get a new router, DSL modem, and ethernet card (the 2Wire is both a router and a modem, if I recall correctly).

---

### Post by british_government on 2005-08-14
nope only the 2 ports, thanks for your help its something i will look into, ebay probably  :-P 
thanks

---

