---
title: "resolv.conf getting overwritten"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by balajig81 on 2007-05-16
I use PPPOEConf for configuring my internet connection. Once my internet connection is configured, the resolv.conf gets updated with proper DNS values but once i reboot my system the resolv.conf gets overwritten with 192.168.1.1 and i dont want my resolv.conf from being modified. I need the values which i configured using pppoeconf to be preserved even after the system is rebooted. How do i stop this resolv.conf from being overwritten ?.

Due to this problem everytime i am made to run pppoeconf after every reboot and configure my internet connection again. 

Thanks
Regards,
Balaji

---

### Post by heimo on 2007-05-16
Possible work-around, remove write permissions:
```
sudo chmod a-w /etc/resolv.conf
```

---

### Post by girishv on 2007-05-16
The resolv.conf file will be overwritten by dhclient.conf. Make the changes you want in the latter file and it will be preserved over reboots

I changed the following two lines in the file dhclient.conf

supersede domain-name "mydomain.com"
prepend domain-name-server xxx.xxx.xxx.1, xxx.xxx.xxx.2

Girish

---

