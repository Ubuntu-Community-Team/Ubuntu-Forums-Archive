---
title: "WG111T usb stick problem"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by Hobbiter on 2008-08-28
Hi there, i have got Windows XP and lately Ubuntu (i am loveing it :) ). and i have just bought a Netgear WG111T USB stick which works perfectly on my XP os. but in Ubuntu i got problem.

i installed it and i can run it. But when i scan for wlan0 it only finds other routers not mine. when i change channel of my router to less than 11 (something like 10 or 7 or even 1) it finds my SSID but when i try to connect to it. it does not accept my password. but i am 100% sure i entered the right password. my password is coded in WPA-PSK.

i thought it was my driver or something i looked around and i tried everything but with no success. can you help me out with this problem. i really want to run Ubuntu on internet instead of switching each time from ubuntu to xp. 

thanks


=========================================================================

i ve solved the problem:

i changed the key encription as it seems that ubuntu does not support WAP (?). i changed it to WEP (Hex coded of 128 bytes).

i also changed the channel to 11 (you can change it between 1 and 11) as it seems that my adapter does not cache channel 13 in ubuntu even when i changed it with this code:

sudo iwconfig wlan0 channel 13

PS: try to choose a channel that does not conflict with an other one in your neighborhood.

the problem was also the rate of my adapter config. as i read in an other thread it says that by default the rate is 1Mb/s and suggested to change it to 54Mb/s or more depends on your adapter and router. so i changed it to 54Mb/s with this code : 
sudo iwconfig wlan0 rate 54M
sudo /etc/init.d/networking restart


good luck i hoop that this helps.

---

### Post by markosjal on 2008-08-28
try turning off Encryption and see if you can connect. It could be te encryption mode you are using on the router is incompatible. I do not think Ubuntu supports  the encryption you indicatd

---

### Post by Hobbiter on 2008-08-28
you mean you want me to put my router wide open without a password? i need to secure my network, right?! and i already tried it withot password wide open but the usb does not find my network on channel 13.

---

### Post by Hobbiter on 2008-08-29
i solved the problem.

---

### Post by markosjal on 2008-08-31
Some countries have different channel allocations for WiFi. You need to check that each has in the same Country setting.

In Some Wifi components , it is hard coded

---

