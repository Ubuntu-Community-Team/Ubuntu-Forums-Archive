---
title: "Getting my Wireless to work"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by Marcke on 2008-09-03
Hi,

I installed Ubuntu a while ago, but didn't use it yet, as I cannot use the internet, so cannot use synaptec, ...

So the only way i would start exploring it, is when that works.

I have TKIP/AES encryption on my wireless router, prevent it from broadcasting its SSID and have a MAC-filter.

Where in Ubuntu do I add this information to make it work?

I prefer not to have to much command line instructions, as I like to know what I'm doing.

Thanks for your help!

Wannes

---

### Post by Peter09 on 2008-09-03
If Ubuntu has detected your wireless card you should have a network icon top left. Right click on that to get more information. Or go to System->Administration->network

---

### Post by falcon61102 on 2008-09-03
I can understand where the command line can get confusing but believe it or not, it's the easiest way to convey directions over the forum.  That being said, I'll try to descibe in detail what the command does so that not only will you know what's going on but you'll learn how to fix it in the future.

As Peter09 said, if your card is detected and works out the box you should be able to see the access points listed when you click on the network manager but if you don't see anything there then it may be that you need to install drivers for your card.

If you can't see the wireless access points, it'd be much easier for us to help if we had some information on your card.  Could you run and post the results of:
```
lshw -C network
```

That command has three parts.  The "lshw" stands for list hardware and the -C means class and network is self explanitory.  So basically you are tellin Ubuntu to list all hardware with the class network.

---

