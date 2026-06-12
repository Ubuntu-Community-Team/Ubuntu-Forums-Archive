---
title: "Anyone know how to change wireless card settings?"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by kmb101 on 2008-10-17
I hope someone can tell me how to change my settings on my wireless card. I have Broadcom 4318 using b43 driver. I have tried *iwconfig wlan0 rate 54M*[/I]. It doesn't work. The bite rate is what I need to change. Any help or suggestions are appreciated. Thanks in advance.


kevin@Presario4125:~$ iwconfig wlan0 rate 54M
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wlan0 ; Operation not permitted.
kevin@Presario4125:~$

---

### Post by Bucky Ball on 2008-10-17
> **kmb101 said:**
> 


kevin@Presario4125:~$ iwconfig wlan0 rate 54M
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wlan0 ; Operation not permitted.
kevin@Presario4125:~$

***sudo***  iwconfig wlan0 rate 54M

---

### Post by kmb101 on 2008-10-17
> **Bucky Ball said:**
> ***sudo***  iwconfig wlan0 rate 54M
Thanks I have tried that but it didn't work for me. It just causes my wireless to stop working. I have to reboot computer to get it back.

---

