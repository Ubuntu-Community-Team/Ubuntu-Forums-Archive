---
title: "Ubuntu doesn't see my WiFi"
date: 2014-06-17
forum: Networking &amp; Wireless
---

### Post by przemek5 on 2014-06-17
Hello,

Recently, I've installed Ubuntu on HP Compaq 610. Everythings works fine but WiFi. I tried ifconfig (shows only eth0 and lo), iwconfig (same stuff) and 'sudo ifconfig wlan0 up' (shows error that there no such device). I also looked for similar cases but mostly, more experienced users wanted more individual hw logs so I decided to start this thread. Can you help me with this?

Thank you for all your answears,
Przemek

---

### Post by Bucky Ball on 2014-06-17
Welcome. Please give the output of these three commands, one at a time, and post back the output using ```
 tags, please:

[code]sudo lshw -C network
iwconfig
ifconfig
```

That's should get us started. My wife has one of those laptops running faultlessly so if same wireless card, and that first command will tell us, I can have a look at what her's is running (wireless is faultless). ;)

Presuming you're using 14.04 LTS? Nice to hear everything else 'just worked'. This will work with a little tweaking, too.

PS: Also presuming you are online with a cable? In that case, open the Software Updater, do an update, and then check 'Additional Drivers' (might be 'Hardware Drivers', depending on the release). Anything there for wireless?

---

### Post by przemek5 on 2014-06-17
Hello Bucky Ball, thank you for your response : ) It works! Option with "Software Updater" solved the problem (there was Broadcom card driver which was turned off because of the fact that only producer provided support to this or something like that - dunno how to go back and see what excacly was written there :"D). Thank you very much! : )

PS Yup, 14.04
PS2 My first solved linux problem, hooray! : D

---

### Post by Bucky Ball on 2014-06-17
Excellent news and congrats on your first solved Linux issue! Glad to be of assistance. Please mark as 'solved' by following the second link in my signature below to help others. Enjoy. ;)

---

