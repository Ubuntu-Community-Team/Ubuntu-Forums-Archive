---
title: "Dell Latitude D630 Wifi Issue"
date: 2014-07-29
forum: Networking &amp; Wireless
---

### Post by crowscare863 on 2014-07-29
Hello, I'm new to Linux and this is my first time trying out a Linux distribution. I decided to install Lubuntu onto my Dell Latitude D630 and I can't get the Wifi to work. I tried some of the suggestions that I found on this forum, one of them to install the broadcom drivers which didn't work. 

Please Help

---

### Post by mörgæs on 2014-07-29
Welcome to the fora.

Moving your thread to Networking and Wireless. Please read the sticky notes.

---

### Post by praseodym on 2014-07-29
Do you know this (bug)?

[http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

If it's not working afterwards, please open a terminal and show the outputs of
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
rfkill list
cat /etc/resolv.conf
```

---

### Post by mörgæs on 2014-07-29
The bug is fixed. If people just install 14.04.1 there's nothing to worry about.

---

### Post by crowscare863 on 2014-07-29
> **praseodym said:**
> Do you know this (bug)?

[http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

If it's not working afterwards, please open a terminal and show the outputs of
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
rfkill list
cat /etc/resolv.conf
```

It was the Wifi bug, once I forced the network app to load the wifi lit up when I logged back in. Thanks a lot!

---

### Post by crowscare863 on 2014-07-29
> **mörgæs said:**
> The bug is fixed. If people just install 14.04.1 there's nothing to worry about.

I downloaded what they had on the front page of the Lubuntu site. I didn't see any other newer versions there.

---

### Post by mörgæs on 2014-07-29
Seems that the Lubuntu page needs an update. 
Anyway, good that you got it solved. Please mark the thread so.

---

