---
title: "unable to connect to wireless despite iwconfig showing the correct details"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by chimanrao on 2007-03-24
hi,

I disabled the wep authentication to check if it is causing the problem.
I restarted the machine and the router.

After the machine started i ran the following command

sudo iwconfig

the fields like essid, access point were empty.

I started wirelesslan assistant, I am on kubuntu 6.10,
it listed my access point, I click on it, I got the message connect failed.

Now if I run 
sudo iwconfig 

the fields like essid, access point are filled up correclty, but wirelesslan assistant is still saying connect failed.

I am not able to ping the router either. I have chosen dhcp option.

Regards
Chimanrao

---

### Post by chili555 on 2007-03-24
May we have a look at:```
sudo iwconfig <your_wireless_interface>
sudo iwlist <your_wireless_interface> scan
```Thanks.

---

