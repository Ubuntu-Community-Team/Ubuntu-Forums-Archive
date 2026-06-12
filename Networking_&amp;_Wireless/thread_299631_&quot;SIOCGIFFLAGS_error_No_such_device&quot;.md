---
title: "&quot;SIOCGIFFLAGS error: No such device&quot;"
date: 2006-11-14
forum: Networking &amp; Wireless
---

### Post by jagman1079 on 2006-11-14
Sorry, i'm kind of new to this, so please any help would be appreciated.
I have a gateway solo 2500 with a combo modem/ethernet card (not wireless).

I have just upgrade from Breezy 5.10 to Dapper 6.01 . The upgrade seems to went well except now my internet is not working. i get the message :
 "SIOCGIFFLAGS error: No such device" 
When i click the monitor applet, in the general tab connection only has lo option. and configure is grey-out. now if i typed eth0 in connection name then status say 'error' but the configure option is able. 

Now i click on configure, the network settings is up.
- connection tab only has the modem option
- general tab has the correct host and domain name
- dns tab has the right configs

By the way i had no problem with 5.10.


I tried iwconfig eth0 : eth0 no such device

now since i don't have internet connection. if it's a driver issue can i install that directly from the hardrive. 

please let me know if you need any console output.

ps: i have read other thread regarding this issue, either they have wireless or there isn't any real answer how to solve it. 

Thank you much.

---

### Post by Iowan on 2006-11-14
If it's not a wireless, try **ifconfig**.  Another option might be **dmesg |grep eth0** to see error messages concerning that device.

---

### Post by jagman1079 on 2006-11-14
I try ifconfig then get info for only 
lo   Link encap:local Loopback and 7 other lines.

and dmesg |grep eth0  didn't get any reply

---

