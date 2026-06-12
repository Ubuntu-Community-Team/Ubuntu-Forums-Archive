---
title: "Cant connect to ad-hoc"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by Kouran-sama on 2008-08-15
hi
heya all, i have the following problem with my ad-hoc connections. i have a embedded linux set up as a ad-hoc node (i can connect to it and ssh via windows, so the thing works) and from my linux box i cant. what im doing arre the following commands: 
```

1) ifconfig wlan0 down 
2) iwconfig wlan0 mode ad-hoc 
3) ifconfig wlan0 up 
4) iwconfig wlan0 essid GumNode01 channel 7

```
after this the LED on the gumnode turns on (which is if something is connected via wlan) but a iwlist on my notebook reveals that the cell is associated with the correct node but link quality is still 0. so even if i give an ip i cant ping.
it somehow seems like they are associated but cannot establish a connection like if you connect to a wep point but dont have the key. the connection between the node and the laptop isnt encrypted.

thanks in advance
tom

-------------------------------------------------------
PS: what i did on the embedded to set up the connection was the same like the code trying to connect, but i also gave it a ip with ifconfig.

---

### Post by dca on 2008-08-15
Look at the bottom of this list and see if your card w/ nm can use ad-hoc.
 
[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

---

### Post by Kouran-sama on 2008-08-15
ad-hoc works for me with notbook to notebook connection. i already used it under ubuntu. thanks for the hint though.

cheers
tom

---

