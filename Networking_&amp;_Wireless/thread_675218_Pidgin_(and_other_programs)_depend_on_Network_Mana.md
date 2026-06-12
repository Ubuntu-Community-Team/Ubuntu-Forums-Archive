---
title: "Pidgin (and other programs) depend on Network Manager?"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by mickeelm on 2008-01-22
Hi.

I have a Netgear WG111T wireless dongle which itself was quite challenging to get to work but thanks to some nice souls here on the forum I've got it to work.

However, if I try to connect with Network Manager it works about every 20th time or something and the computer usually freezes after a while. So, I use this when I connect:

```
sudo iwconfig wlan0 essid networkname
sudo dhclient
```

This works perfectly as far as connecting to the internet and so on. However, Pidgin for example doesn't realize that I am connected so I have to deactivate my MSN account and then activate it again every time i login to "fool the program". Even after that, It says "waiting for network" or "waiting for connection" (I have a swedish version so I do not know the exact translation) even though I am connected.

I could live with that, but for example when I tried aMSN it only thought that I was offline all the time and I could not connect, so I guess I will have this problem with other programs in the future as well...so therefore, my question is if anyone knows how to change this, so that programs do not check with network manager but with for example iwconfig if I am connected or not?

---

### Post by mickeelm on 2008-01-23
I sort of solved the problem by uninstalling Network Manager...which indeed solved the issues with Pidgin and aMSN, but I was hoping to have another solution so I could keep Network Manager as it works fine with cable connection.

Anyone that knows how to fix my problem without having to remove NM is welcome to share that info :)

---

