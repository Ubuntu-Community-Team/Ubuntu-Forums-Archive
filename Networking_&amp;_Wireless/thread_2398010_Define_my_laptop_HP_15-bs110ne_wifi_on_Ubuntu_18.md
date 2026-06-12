---
title: "Define my laptop HP 15-bs110ne wifi on Ubuntu 18"
date: 2018-08-06
forum: Networking &amp; Wireless
---

### Post by astm2 on 2018-08-06
[COLOR=#000000][FONT=HPRegular]Dear All,[/FONT][/COLOR]
[COLOR=#000000][FONT=HPRegular]How I can define my laptop **HP 15-bs110ne** wifi on Ubuntu 18 ?!!
I tried to search about the driver but didn't find anything, and HP website it's only giving me the windows drivers !!![/FONT][/COLOR]


[COLOR=#000000][FONT=HPRegular]Regards[/FONT][/COLOR]

---

### Post by jeremy31 on 2018-08-06
Please see the wireless script link in my signature and post results

---

### Post by astm2 on 2018-08-07
Hi Jeremy31,
I followed the steps in this post [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
But still got the same issue
do you have any idea to fix it?!

---

### Post by astm2 on 2018-08-07
The Additional driver screen is empty list
#Help #HP #Wifi #Ubuntu

[IMG]https://image.ibb.co/cA3ZgK/Screenshot_from_2018_08_07_10_35_05.png[/IMG]

---

### Post by jeremy31 on 2018-08-07
Post results from terminal for ```
lspci -nnk | grep -iA3 net
```

---

