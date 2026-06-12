---
title: "Cant connect to a network with the Broadcom 4318 chip set"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by 11zac11 on 2008-11-13
hello all it has been a while since i have need the help of this amazing forum but im back again with a different WLAN Problem. 
After how please i was with getting my laptop to run ubuntu 8.04 i decided this week to try ubuntu 8.10 on my desktop which is a dell inspiron 531 and has the a wireless card based on the Broadcom 4318 chip set. 
After playing around with it i have yet to be able to get my wireless card to connect to a network, i have tried to use ndiswrapper but can not find the windows drivers for this chip set. So i was wondering if someone out there either can give me a link to the files i need or knows of a different way to go about it. Thank you all :)

---

### Post by pinau on 2008-11-15
the same problem :(

---

### Post by superprash2003 on 2008-11-15
hope this helps [http://prash-babu.blogspot.com/2008/11/how-to-configure-broadcom-wireless-in.html](http://prash-babu.blogspot.com/2008/11/how-to-configure-broadcom-wireless-in.html)

---

### Post by 11zac11 on 2008-11-15
i read that and tryed to do as it said but the Broadcom drivers are not on the list only my graphics card one which i cant use untill i have the internet.

---

### Post by dedyisn on 2008-11-15
> **11zac11 said:**
> hello all it has been a while since i have need the help of this amazing forum but im back again with a different WLAN Problem. 
After how please i was with getting my laptop to run ubuntu 8.04 i decided this week to try ubuntu 8.10 on my desktop which is a dell inspiron 531 and has the a wireless card based on the Broadcom 4318 chip set. 
After playing around with it i have yet to be able to get my wireless card to connect to a network, i have tried to use ndiswrapper but can not find the windows drivers for this chip set. So i was wondering if someone out there either can give me a link to the files i need or knows of a different way to go about it. Thank you all :)
Hope this can helps u

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by 11zac11 on 2008-11-15
i have tried that and got the drivers installed but it still isnt able to conect to a network or even find any

---

### Post by Marius Derekus on 2008-11-15
Check this forum out: [http://ubuntuforums.org/showthread.php?t=981607](http://ubuntuforums.org/showthread.php?t=981607) Comment #7


Note: My chipset was boradcom 4312, so i don't know if this will work for yours.

---

### Post by Marius Derekus on 2008-11-15
Let me know if it works.:KS

---

### Post by Marius Derekus on 2008-11-15
This thread seemed overwhelming to me  but it might help
[http://ubuntuforums.org/showthread.php?t=870086](http://ubuntuforums.org/showthread.php?t=870086)

---

### Post by Marius Derekus on 2008-11-15
Ignore the above thread, i didn't know that it was already posted by another user. Sorry :lolflag:

---

### Post by 11zac11 on 2008-11-15
looked over that and it dosnt work when i go into the diver thing like i have already said it just has my graphics card driver

---

### Post by Marius Derekus on 2008-11-15
This might help: [http://ubuntuforums.org/showthread.php?t=265284](http://ubuntuforums.org/showthread.php?t=265284)

I think the driver your looking for might be bcmwl5.sys but i don't know. Try googling it. (Make sure to get the bcmwl5.inf file as well). If there are any other additional files that go with bcmwl5.sys i don't know what they are. (Maybe a .PNT file or somthing). I think the main file you'll want is the .inf file. Hope it helps.

---

### Post by 11zac11 on 2008-11-16
i have installed the drivers into ndiswrapper and it says there are installed etc but it still dosnt work :(

---

### Post by Marius Derekus on 2008-11-19
ndiswrapper never seems to work on any one. Try checkin **system>administration>hardware drivers** and make sure the card is enabled (if it is listed.

---

### Post by 11zac11 on 2008-11-19
its not even listed thats the problem

---

