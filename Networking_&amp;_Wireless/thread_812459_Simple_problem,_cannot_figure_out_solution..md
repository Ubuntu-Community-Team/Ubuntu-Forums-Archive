---
title: "Simple problem, cannot figure out solution."
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by Kenjitamura on 2008-05-29
So my brother is hooked on ubuntu and used it on his laptop at my house.   He moved a couple states away and now he can't connect to any networks.  He used to use WICD but i had him remove it and go back to network manager.  He lives in an apartment with wireless internet and cannot connect.  I told him to type in "iwlist scan" and the network was shown and listed as no encryption.  I then told him to type in "sudo iwconfig eth1 essid 'nameofnetwork'".  Still not connected.   So i told him to type in just iwconfig and what came up confuses me, it said under eth1 "unassociated essid" bit rate 0.  Under Network Options he has the card enabled, the essid entered, and its set to DHCP.  He uses a sony vaio and i think ipw2200 drivers (but im not certain).  Please help.

---

### Post by scottslinux on 2008-05-29
I wish that I could offer you an answer.  Instead I am out here in the forums with exactly the same problem.  I have Hardy installed and have found that I can connect to wpa wep and ***some*** unencrypted networks. That is the issue. Some unenrypted networks work while others seem to hang up in the "obtaining IP address" stage and eventually time out.  Would be interested in knowing why this happens.  Wireless card works perfectly otherwise. Why is it that a wireless adapter can associate with one open access point and not another?

Scott

---

### Post by lisati on 2008-05-29
Is it possible that the administrators of the unencrypted networks that you can't connect to have set their wireless routers to accept or reject connections based on MAC addresses?


(A MAC address is a unique identifier that's built into the network adapter when it's manufactured)

---

### Post by scottslinux on 2008-05-29
> **lisati said:**
> Is it possible that the administrators of the unencrypted networks that you can't connect to have set their wireless routers to accept or reject connections based on MAC addresses?


(A MAC address is a unique identifier that's built into the network adapter when it's manufactured)

-I am referring to open networks in a coffee shop surrounded by others connecting easily. There is no mac address blocking going on.

Scott

---

### Post by Bubba64 on 2008-05-30
> **Kenjitamura said:**
> So my brother is hooked on ubuntu and used it on his laptop at my house.   He moved a couple states away and now he can't connect to any networks.  He used to use WICD but i had him remove it and go back to network manager.  He lives in an apartment with wireless internet and cannot connect.  I told him to type in "iwlist scan" and the network was shown and listed as no encryption.  I then told him to type in "sudo iwconfig eth1 essid 'nameofnetwork'".  Still not connected.   So i told him to type in just iwconfig and what came up confuses me, it said under eth1 "unassociated essid" bit rate 0.  Under Network Options he has the card enabled, the essid entered, and its set to DHCP.  He uses a sony vaio and i think ipw2200 drivers (but im not certain).  Please help.

Strange as it may seem the Hardy network manager has a roam option in the wired setting, I assume your brother is wired rather than wireless. It may be that if he is using wireless that setting both to roam will get the addresses in that are needed. Also I can almost never get my computer to connect with wireless after a disconnect without accessing my own network via roam or a restart if on manual.

---

