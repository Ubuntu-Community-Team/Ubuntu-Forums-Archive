---
title: "How to install downloaded wifi driver"
date: 2019-04-30
forum: Networking &amp; Wireless
---

### Post by morcielago on 2019-04-30
Hey guys I have downloaded my laptop (dell latitude d600) Wifi driver and it is this link 

```
https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-2000-ucode-18.168.6.1.tgz

```
there is 3 files and i don't know How can i install it 

please help me

---

### Post by jeremy31 on 2019-04-30
Please see the wireless script link in my signature and post results as iwlwifi firmware is included in Ubuntu

---

### Post by chili555 on 2019-04-30
I downloaded and extracted the referenced file. It contains the firmware file  iwlwifi-2000-**6**.ucode. However, the most recent versions of linux-firmware also contains it; confirm:```
ls /lib/firmware | grep 2000
```If your wireless is not working correctly, it is not the firmware at fault.

Once Jeremy examines the results of the wireless script he requested, he'll know more. Also, please describe in detail the trouble you're having.

---

### Post by morcielago on 2019-04-30
> **chili555 said:**
> I downloaded and extracted the referenced file. It contains the firmware file  iwlwifi-2000-**6**.ucode. However, the most recent versions of linux-firmware also contains it; confirm:```
ls /lib/firmware | grep 2000
```If your wireless is not working correctly, it is not the firmware at fault.

Once Jeremy examines the results of the wireless script he requested, he'll know more. Also, please describe in detail the trouble you're having.


So what can I do exactly?
Unfortunately I don't have Ethernet internet connection
I want to fix my problem in offline mode

---

### Post by chili555 on 2019-05-01
Please describe in detail what trouble you are having.

---

