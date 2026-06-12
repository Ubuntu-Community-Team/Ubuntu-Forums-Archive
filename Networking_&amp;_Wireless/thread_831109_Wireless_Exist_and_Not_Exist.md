---
title: "Wireless Exist and Not Exist"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by jotnarta on 2008-06-16
Hi All

I have a wireless network at my home, when I go to my work, I change the connection to be a static IP and a proxy. Yesterday, I connected to wireless network and the signal was excellent. But today, when I tried to connect I couldn't.

The strange thing is that my laptop detected the wireless, and when using (iwlist scan) command, it shows that it exist and detected, but I can't browse.

Besides, I removed the wired connection from the network manager, but the network icon don't change in the task bar, it always displays the wired connectioin icon, and not the wireless despite that I choose the wireless network

Why? any help please?
Jotnarta

---

### Post by pytheas22 on 2008-06-16
You can create different profiles for the wireless connection for work and home by using the Network utility found at System>Administration.  You could also try using [wicd]("http://wicd.sourceforge.net"), which will do the same thing.

As for your connection failing at home: first try bringing your interface down and back up and see if you can connect, e.g.:
```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```

(note that your interface might not be called "wlan0"; it may be eth1 or ath0 instead, or something else).

If that doesn't work, does rebooting the computer fix the problem?

If not, please post the output of these commands when you are trying to connect at home and are unable:
```

iwconfig
ifconfig
```

---

