---
title: "iwl3945 / network manager on Hardy make me write from Windows... :-("
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by puccio on 2008-06-15
Hello,

I have Ubuntu Hardy on a Dell Inspiron 6400. Before Hardy, everything worked fine using the kernel 2.6.22 and the ipw3945 driver.

When I dist ugraded, booting with the new supplied kernel 2.6.24-something and using hence the iwl3945 driver, my network manager in Gnome did not list any wireless network, so I  simply booted with the old kernel and the ipw3945 and everything was fine.

Now since some days even booting with the old 2.6.22 kernel the network manager even if it finds the wireless AP, it does not connect to it.. (it's a WPA or WPA2).

For the sake of informations, booting with 2.6.24 and using iwl3945, I can iwlist eth1 scan succesfully but network manager -as I said- simply finds no networks...

I'm getting quite frustrated, I've googled around and found many different replies to the problem and getting lost...and now I even have to write from Windows to be able to access the forum..](*,)

Looking forward for some info, thank you guys

---

### Post by 7he on 2008-06-15
Please try this:
Enable Proposed and backports repositories [1], then upgrade.


[1] System &#8594; Administration &#8594; Software Sources -> Updates

---

### Post by puccio on 2008-06-15
Hi, thanks for your reply.

Backports installed, now in network manager I manage to find the wireless network but it allows me just to type ASCII/Hex key for **only WEP**, while instead the access point is WPA 1...

What's missing?

---

### Post by IvanIvan on 2008-06-15
AFAIK, you're having a known problem with Hardy+iwl3945+network manager+WPA/WPA2 combination. :)
I have the same wlan card and iwl3945 and I removed network manager and installed wicd and so far it works.
this was my problem:
[http://ubuntuforums.org/showthread.php?t=826923](http://ubuntuforums.org/showthread.php?t=826923)

---

### Post by puccio on 2008-06-15
Man, I owe you a beer, I'm back on Linux! :KS

The trick was indeed to use wicd, which by the way seems to me very nice, I wonder why it is not the default one..

Thanks again, ciao!

---

### Post by IvanIvan on 2008-06-15
> **puccio said:**
> Man, I owe you a beer, I'm back on Linux! :KS

The trick was indeed to use wicd, which by the way seems to me very nice, I wonder why it is not the default one..

Thanks again, ciao!
no problem, glad it works. :popcorn:

---

