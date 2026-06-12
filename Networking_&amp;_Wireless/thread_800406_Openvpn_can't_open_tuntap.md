---
title: "Openvpn can't open tun/tap"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by EoRaptor013 on 2008-05-19
I've installed openvpn on Hardy following the instructions [here]("http://openvpn.net/index.php/documentation/howto.html") for the general configuration and [here]("http://openvpn.net/index.php/documentation/miscellaneous/ethernet-bridging.html") for setting up ethernet bridging. When I try to start openvpn, I get this error message:

Sun May 18 22:11:47 2008 Note: Cannot ioctl TUNSETIFF tap0: Device or resource busy (errno=16)
Sun May 18 22:11:47 2008 Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Sun May 18 22:11:47 2008 Cannot open TUN/TAP dev /dev/tap0: No such file or directory (errno=2)
Sun May 18 22:11:47 2008 Exiting
SIOCADDRT: No such process

These messages were repeated two seconds later, then return to the command prompt. 

FWIW, both br0 and tap0 (oh yeah, I set up the server.conf with dev tap0) show activity in Gkrellm. 

Any thoughts, pointers, or suggestions would be greatly appreciated. 

EoRaptor

---

### Post by EoRaptor013 on 2008-05-19
Umm, while I'm at it, can somebody 'splain to me why Linux won't recognize the second lan card I put in? Dropped the card in another computer (with that other OS) and it seems to work fine. Even device manager has no idea it's there. The card is a Linksys 10/100 LNE100TX. 

Thanks.

EoRaptor

---

### Post by SpaceTeddy on 2008-05-20
how did you create the tap device and how did you bond it together with a network card ? can you please show the output of 

```
ifconfig
brctl show
```

my first guess was that you forgot to start the openvpn process as root - but that is not the error which i get when i start it as non-root.
So my second guess is that you either created the tap0 wrong or there is a second openvpn process. can you please check that with:
```
ps aux |grep openvpn
```

hope we can figure this :)

---

