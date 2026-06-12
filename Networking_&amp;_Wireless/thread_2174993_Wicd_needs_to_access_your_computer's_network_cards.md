---
title: "Wicd needs to access your computer's network cards"
date: 2013-09-17
forum: Networking &amp; Wireless
---

### Post by f0olyc0oly on 2013-09-17
I'm replacing the network manager on Ubuntu 13.04 LXDE with WICD due to disconnecting issue on the Wireless.

After installing WICD and rebooting, this message keeps popping up. ```
"Wicd needs to access your computer's network cards"
```

Any advice?

---

### Post by varunendra on 2013-09-17
Have you seen [this]("http://askubuntu.com/questions/293049/wireless-n-networks-in-ubuntu-13-04-and-wicd") ? If your's is a different card, please show us which one it is -
```
lspci -nnk | grep -iA2 net
```


**EDIT:**
Just read this bug report : [https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/1132529](https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/1132529)
Maybe try the solution suggested in comment #22 first.

---

### Post by f0olyc0oly on 2013-09-17
> **varunendra said:**
> Have you seen [this]("http://askubuntu.com/questions/293049/wireless-n-networks-in-ubuntu-13-04-and-wicd") ? If your's is a different card, please show us which one it is -
```
lspci -nnk | grep -iA2 net
```

This is the result:
```
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 3e)
```

I did the below steps as well

```
gksudo gedit /etc/modprobe.d/iwlwifi.conf

options iwlwifi 11n_disable=1
```



**EDIT:**
Just read this bug report : [https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/1132529](https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/1132529)
Maybe try the solution suggested in comment #22 first.[/QUOTE]


I tried comment #22, wow it worked finally! Thanks very much for your help! ;):D;):D

```
bmarsh, your patch provided in comment #19 fixed it for me. I did this:

    rm /etc/resolv.conf
    ln -s /run/resolvconf/resolv.conf
    rm /var/lib/wicd/resolv.conf.orig
    ln -s /run/resolvconf/resolv.conf /var/lib/wicd/resolv.conf.orig

then, launching wicd with "sudo service wicd start" worked, and wicd-gtk appears to be functioning normally. I'm not experiencing anything with wpa2 malfunctioning.

```

---

### Post by varunendra on 2013-09-18
Cheers ! :popcorn:

..And I learnt something new about wicd (never tried wicd myself anyway)

Thanks for the feedback ! Please mark the thread as [SOLVED] (using the link in the "Thread Tools" above the top post), it helps others looking for help on similar issues. :)

---

