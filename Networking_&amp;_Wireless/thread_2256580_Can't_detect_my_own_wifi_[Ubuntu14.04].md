---
title: "Can't detect my own wifi [Ubuntu14.04]"
date: 2014-12-13
forum: Networking &amp; Wireless
---

### Post by dexter16 on 2014-12-13
hi,

After installing the Ubuntu14.04 LTS, my network-manager is unable to detect my own wifi. Instead i am able to see some other wireless APN's of my neighbours. Already checked by restaring the router and network manager. Also checked the output of  **sudo iwlist wlan0 scan. ** it doesn't enumerates my wifi APN. Also checked the possibility of multiple driver issues (not there)

Thanks in advance

---

### Post by howefield on 2014-12-13
Thread moved to the "Networking & Wireless" forum where it is more likely to get help than it would in the Resolution Centre.

---

### Post by jeremy31 on 2014-12-13
What channel is your router on?  And in terminal enter ```
iw reg get
```

---

### Post by ajgreeny on 2014-12-13
Is your router broadcasting the SSID of the wireless output; it may be hidden for some reason.

---

### Post by dexter16 on 2014-12-14
output of **iw reg get**:
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

Regarding the Broadcast of SSID. i am able to connect to the same wifi APN via Windows (i have dual partition with Linux and Windows) and my phone. I think it is broadcasting correctly. Please correct me if i am wrong here.

---

### Post by ajgreeny on 2014-12-14
Do you see the name of that wireless connection in your Windows OS or were you already set up with a connection to it in Windows?
Can other guests to your home see the wireless with its name listed?

---

### Post by dexter16 on 2014-12-15
Yes i am connected to the wireless APN via Windows. in windows the guest accounts are able to detect the wireless. In linux it is not being detected even by other guest users also.

---

### Post by ajgreeny on 2014-12-15
What brand of router is it; it may be worth searching that "router-model linux" to see if you get hits of other users having linux problems, though as far as I'm aware it is not the router that presents problems normally but the wireless adapter on the client machine.

---

### Post by dexter16 on 2014-12-15
Its a Binatone router Model: DT 850W

---

