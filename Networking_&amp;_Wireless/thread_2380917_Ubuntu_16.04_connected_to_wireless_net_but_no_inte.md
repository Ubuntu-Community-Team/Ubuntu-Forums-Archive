---
title: "Ubuntu 16.04 connected to wireless net but no internet"
date: 2017-12-23
forum: Networking &amp; Wireless
---

### Post by juaninsantiago on 2017-12-23
Hi everybody!

I have a problem with my wireless connection, it appers that i am connected but i can't use internet, also i can't ping any IP or resolve any page name.
The result of the wireless-script is here:
[https://pastebin.com/qk4B9Cgk](https://pastebin.com/qk4B9Cgk)

Thanks everybody :)

---

### Post by jeremy31 on 2017-12-23
Follow chili555's instructions on [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
You do have your country code set correctly but power management is enabled and your wifi router is using TKIP

---

### Post by juaninsantiago on 2017-12-23
I made a mistake, i was connected to another network that works.
Mine is still not working, i changed from TKIP to AES and disabled power management

---

### Post by jeremy31 on 2017-12-23
I would reboot, try connecting to wifi, wait 5 minutes and do
```
./wireless-info
```
Connect with ethernet and post the new script results

---

### Post by juaninsantiago on 2017-12-23
here is the new script results
[https://pastebin.com/wn2AcZGh](https://pastebin.com/wn2AcZGh)

---

### Post by jeremy31 on 2017-12-23
Go into Network Manager settings and set Ipv6 settings to ignore for all connections, have to do it one connection at a time

---

### Post by juaninsantiago on 2017-12-23
do you mean for every SSID i have stored??

---

### Post by jeremy31 on 2017-12-23
For at least the ones you use.  There was an error about duplicate IPv6 addresses in the last results

---

### Post by juaninsantiago on 2017-12-23
i did it but still not working, should i run the script again?

---

### Post by jeremy31 on 2017-12-23
Sure

---

### Post by praseodym on 2017-12-24
Please try
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi-11n.conf
```
Reboot

---

