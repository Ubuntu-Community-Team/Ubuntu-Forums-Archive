---
title: "Can't connect to internet"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by Planetes on 2010-07-30
I'm currently traveling and can't connect my laptop through either wireless or a lan. I have never had trouble before but i have also never tried to connect to another network before. It detects several different networks just fine, it just refuses to connect.

---

### Post by Naitsirhc Hsem on 2010-07-30
for lan, try ```
sudo ifconfig eth0 up
``` then ```
sudo dhclient
```  eth0 is your ethernet card, you can see all of the possibilities if you type in ```
ifconfig
```  if the wifi is not encrypted, you can do something similar, ```
sudo iwconfig wlan0 essid "Network Name" 
sudo dhclient
```

---

### Post by Planetes on 2010-07-30
So those are supposed to connect me to the network? or are they just tests to find out whats wrong?
 
Yes the networks are open i am at a hotel, have been at two different ones now so the problem was not isolated.
 
Thanks for the response.

---

### Post by Planetes on 2010-07-30
I tried the steps for the wireless and got nothing. The output from the end of it said "no DHCP offers recieved" and "no working leases in persistent database - sleeping"
 
I was told this might mean that i am not being offered an ip address from the network.

---

