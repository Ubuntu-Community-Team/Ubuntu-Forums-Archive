---
title: "How to enable wireless"
date: 2014-05-15
forum: Networking &amp; Wireless
---

### Post by Steven_Faraday on 2014-05-15
Hi,
I am new to Ubuntu and I have installed Ubuntu 14.04 LTS I am not able to enable wireless. I don't even see the option under the network manager. I have tried quite a few different things but none of them have worked. I am using the Linksys Wireless-N USB adapter (Model AE2500). According to what I can see- this adapter is supposedly, supported as part of default install. I have spent an awful lot of time on this issue and I have gotten pretty frustrated. Sure could use some help. regards...

---

### Post by cariboo on 2014-05-16
The first thing you need to do is to make sure your device is detected, and the correct driver loaded. THe following command will give you the needed information:

```
sudo lshw -C network
```

Also moved to networking and wireless

---

