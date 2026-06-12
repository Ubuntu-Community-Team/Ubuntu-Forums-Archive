---
title: "iwconfig wont let me set mode to master"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by nvysel24 on 2008-04-02
my linksys ver 4 class 2 prism chipset wont let me set it to mast and i dont know why
the code below is what i do and then the results of what i do. is there anything that i can change or do differently?
sudo iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

---

### Post by kevdog on 2008-04-02
Not sure if that driver allows the card to be set to master mode.  In fact, the devices I can think of that can be set to master mode are atheros and some ra chipsets, but not the realtek or prism chipset.  Can you confirm your device can be set to master mode?

---

### Post by nvysel24 on 2008-04-02
well i think it can be set to master cuz i tried seting my integrated wireless to master and it said operation not supported and with this one it jus says invaild argument so to me that means its supported also i looked on youtube and this guy was able to set wlan0 to master but it was a different card

---

