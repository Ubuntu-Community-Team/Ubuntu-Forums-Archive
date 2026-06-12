---
title: "Can't connect to password protected wifi in Ubuntu 15.04"
date: 2015-08-07
forum: Networking &amp; Wireless
---

### Post by Revolutionary101 on 2015-08-07
Hello there!

I am unable to connect to password protected wifi. Its as simple as that but unfortunately, I can't seem to find a solution online. Currently, I can edit all the information in the wireless network properties such as network encryption, password, user name, etc. but I can't click the connect button on the bottom because it seems to be grayed out. With my scouring the internet for a solution I came upon [http://askubuntu.com/questions/614922/15-04-cant-connect-to-password-protected-wifi](http://askubuntu.com/questions/614922/15-04-cant-connect-to-password-protected-wifi) but it seems that person did not have their question answered. Additionally, through my looking around some people seem to have mentioned that it was a permissions issue but I can't find a way to fix it. Any help would be appreciated. Thanks!

---

### Post by TheFu on 2015-08-08
What does **rfkill list** output? Anything locked?

---

### Post by Revolutionary101 on 2015-08-10
This is the output of rfkill list. The weird thing is that I can connect to password protected wifi as long as I set up the network configuration before I upgraded to 15.04.

```

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

---

### Post by Revolutionary101 on 2015-08-17
bump

---

