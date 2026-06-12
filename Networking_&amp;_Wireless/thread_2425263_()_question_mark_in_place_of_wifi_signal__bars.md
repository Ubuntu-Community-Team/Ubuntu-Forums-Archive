---
title: "(?) question mark in place of wifi signal  bars"
date: 2019-08-22
forum: Networking &amp; Wireless
---

### Post by gamesbledsoe on 2019-08-22
my acre R15,  wifi is giving me fits, I can log on to wifi networks but only get errors when trying to access the web and there is a question mark where one expects to see signal bars
ping goggle.com from  the command line returns "system error"

---

### Post by Xian on 2019-08-22
You didn't mention what Ubuntu version is being used but generally if you goto:

Settings > Privacy > Connectivity Checking

Set it to be off. After either restart your WiFi connection or reboot.

---

### Post by gamesbledsoe on 2019-08-23
Hi thanks,  I am running  18.04.2 LTS  that didn't work  my 
DNS 75.75.75.75.75.75.76.768.8.8.8 gets me no where
i see here i am missing a "."    between 76 and 8  
i tried to network to a windows machine when this problem happened  and i have set the laptop aside for a couple of months 
in the terminal  i have gotten to; /ect/netplans$    i am stalled here
   ls command gives;  01-network-manager-all.yaml

---

### Post by QIII on 2019-08-23
Do you mean 

75.75.75.75 75.75.76.76 8.8.8.8

---

