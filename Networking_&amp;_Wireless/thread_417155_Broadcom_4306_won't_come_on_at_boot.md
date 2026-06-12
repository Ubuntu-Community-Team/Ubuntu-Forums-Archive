---
title: "Broadcom 4306 won't come on at boot"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by rich.bradshaw on 2007-04-21
Hi,

I ndiswrapped my drivers, and card works fine, but only if I type

sudo ifconfig wlan0 up

After that it brings up the keyring password thing, and then it works. How can I make this work straight away without having to type this line?

Weird thing is, the card appears as eth1, but if I type the above with eth1 it doesn't work...

Any one know?

---

### Post by Chuklz on 2007-04-21
alright, open up a terminal and type
```
sudo gedit /etc/modules
```

this will open up the modules that will load at boot time

next, add a line that says
```
ndiswrapper
```
then restart

let me know if this fixes your problem

---

### Post by rich.bradshaw on 2007-04-22
Genius!

Thank you!

---

