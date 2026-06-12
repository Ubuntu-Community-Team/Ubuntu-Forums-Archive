---
title: "WLAN not working after installing Ubuntu 18.04 on HP Pavillion 15"
date: 2018-06-01
forum: Networking &amp; Wireless
---

### Post by anachronos2 on 2018-06-01
I tried to make it work using browser updates, but it turned out that the network adapter was hard blocked after running *rfkill list all*. I'm currently running a dual boot with Windows, where the adapter works fine. 
```

rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

I used the script from the network subforum sticky and got the following results: 
[https://pastebin.com/wgF27vaf](https://pastebin.com/wgF27vaf)

---

