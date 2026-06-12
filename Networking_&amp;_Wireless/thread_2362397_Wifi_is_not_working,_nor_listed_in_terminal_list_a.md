---
title: "Wifi is not working, nor listed in terminal list all command result."
date: 2017-05-28
forum: Networking &amp; Wireless
---

### Post by aksh2143 on 2017-05-28
I have recently installed ububtu. So obviously i am not able to enable my wifi  connection. I have tried updating ubuntu and additional drivers as well. But all i got is a bluetooth option. :( I tried 'list all' command in terminal. But there was only bluetooth connection listed. Does this mean i will never be able to use wifi in ububtu? Any help please.....

---

### Post by blackbird34 on 2017-05-28
Which computer model do you have? 

Do you have a hardware switch on your computer that turns the wifi off? 

Have you looked in the Network menu on the top panel (the one that has arrows on it) to see if wifi is disabled? 

Have you checked System settings > Network, to see if there are any available networks, or if your wifi card is turned off? 

 [IMG]https://www.howtogeek.com/wp-content/uploads/2014/10/01_selecting_system_settings.png[/IMG]

Or else, could you post the output of the lspci command? It will list all your computer components including network cards.  ```
lspci
```

---

### Post by howefield on 2017-05-28
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by chili555 on 2017-05-28
> Does this mean i will never be able to use wifi in ububtu? No. It simply means that we need to identify your wireless device and install a driver. Please start here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

