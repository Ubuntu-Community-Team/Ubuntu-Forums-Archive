---
title: "Random network connection problems"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by Hachi-Roku on 2008-03-01
Hey.

using gusty, on dell 510m laptop with wireless internet setup

Usually my wireless internet works sweet. In general everything 'seems' to be setup correctly.

However, maybe 3 out of 10 times; i'll switch on my router then my laptop but ubuntu doesnt seem to be able to connect to the net. Regardless of how many times have been successful.

This mainly happens when i have logged into gusty BEFORE booting up my router. Or if my router decides to drop out..sometimes gusty doesnt get the connection back.

I normally fix this by restarting.. sometimes 2 or 3 times. Or i get fed up and boot into windows.

Im not awesome with linux networking yet but i seem to see that some kind of net connection thing has to be restarted for it to work

In researching, i found this on another thread;
```
sudo /etc/init.d/networking restart
```

It seems like this would restart networking adapters... yet to try it, but can someone tell me if im on the right track??

cheers

---

### Post by mrsteveman1 on 2008-03-01
Restarting the networking scripts should help most of the time, unless the card has a weird bug and has to have its driver/firmware reloaded (which is what youd be doing by rebooting).

What chipset is this wlan chip? Do you know?

Run lspci if you don't know

---

