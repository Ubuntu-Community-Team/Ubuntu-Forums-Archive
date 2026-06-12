---
title: "wifi connection lost"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by nhutto on 2007-11-07
so every time i log into ubuntu 7.10 i have to go into my network configuration and uncheck and recheck my wireless connection so that i get actual service i was wondering how i can fix it i am open to any idea even if some one has a script that will do those actions for me so i don't have to keep messing with it cause it is kinda tedious.

---

### Post by nhutto on 2007-11-08
i found the command that will do the same action for me and it works but how do i get it to run automatically 

```
sudo ifup wlan0 --force
```

---

### Post by Waistless on 2007-11-08
Go to System -> Preferences -> Sessions

You should be at Startup Programs, click +Add and place that command in the command box, give it a name and add it :popcorn:

---

