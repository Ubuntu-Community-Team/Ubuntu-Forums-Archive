---
title: "USB Wireless"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by SwiftDestiny on 2010-02-26
Hi Guys,

Struggling a bit with my new Ubuntu install, I can't make my wireless internet work and much too far away from the router for my cable to reach.

Found out how to install my adapter (WG111v3) using something called ndiswrapper, but obviously Ubuntu has no internet to be able to download this. How do I download this on my Windows partition so I can take it across with a flash drive?

Cheers :)

---

### Post by Peter09 on 2010-02-26
This adapter should work on a plug and play basis. Try booting with the adapter in and post the output of the terminal command
 
```
lsusb
```
 
and
 
```
ifconfig
```

---

### Post by SwiftDestiny on 2010-02-26
Wow!

I don't know what the hell I was doing haha. I just saw the network icon with 2 dash's and assumed all was not working, didn't realise clicking it would show me a list of networks.

In my defence the last time I used Linux was a few years back and stuff wasn't this simples!

---

