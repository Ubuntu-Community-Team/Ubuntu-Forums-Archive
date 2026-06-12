---
title: "Nortek PCMCIA wirless adapter"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by grispa on 2007-06-30
Greetings!
I have been using Ubuntu for almost two months now and I am very satisfied with it. Windows is a nightmare, now, I hope I will not see again.
But. The great obstacle to linux spread, i.e. hardware support, is now taking its toll.
The problem is a PCMCIA Wireless adapter by Nortek. It is a pretty old card, slow (11Mb/sec), but is still my only way, until I get more money, to connect to my wireless network at home.
Now, included in the original driver cd there are two drivers for linux, respectively for RedHat 7.3 and 9.0 (told you it is old..!).
My question is: is it possible those drivers to work under Ubuntu? And if not, as I suspect, is it possible to adapt them to it? Ad if it is, who may I ask to do that?
In case this is too much trouble, as final question, if I decide to buy a new adapter, what brand/model would you suggest?
Thank you for your attention. I hope to hear from you soon. ;)
Paolo

---

### Post by chili555 on 2007-06-30
> is it possible those drivers to work under Ubuntu?Very doubtful. Let's get a better fix on what we are actually dealing with first. Pop that card in the slot and issue a command:```
sudo lshw -C network
``` Please post the output here and we'll see if we can get you going.

---

