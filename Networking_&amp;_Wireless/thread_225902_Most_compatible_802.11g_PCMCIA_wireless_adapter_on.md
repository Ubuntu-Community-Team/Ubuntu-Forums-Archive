---
title: "Most compatible 802.11g PCMCIA wireless adapter on Ubuntu?"
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by ozy on 2006-07-30
Hello there,

I have dabbled with Ubuntu on my desktop and would now like to install it on my Laptop, which will be connected wireless through a Netgear DG834G Router with WPA encryption. My Netgear PCMCIA card has recently failed and so I am taking the opportunity to replace this with a "known working" adapter for Linux. My question is this:

Is there an 802.11g PCMCIA wireless adapter that is known to be compatible with Ubunutu 6.06 Dapper Drake, supports WPA encryption and works "out of the box"? I am not averse to a little fiddling to get it to work, but the more automated the install, the better.

If such a thing does not exist, then could anyone provide the most "suitable match" to the above requirements.

Thanks a lot,

Chris

---

### Post by x64Jimbo on 2006-07-30
I highly recommend cards that are built on the Atheros chipset. Search around and you can find them. They use the open source Linux driver "madwifi" and are quite good at "working out of the box"
WPA is a different issue. It doesn't work very well in Linux no matter what you do. wpa_supplicant is kind of sloppy and doesn't stay connected very well. You're welcome to try it out, but I didn't want you to get your hopes up.

---

### Post by ozy on 2006-07-30
Thanks for the reply Jim, i'll certainly take a look into cards with the Atheros chipset, however I wouldn't really want to compromise the security of my home network by going back to WEP so I may leave it for now until WPA support is more mature.

Chris

---

### Post by x64Jimbo on 2006-07-30
I'd recommend trying out wpa_supplicant with a LiveCD and see if it works for you.

---

