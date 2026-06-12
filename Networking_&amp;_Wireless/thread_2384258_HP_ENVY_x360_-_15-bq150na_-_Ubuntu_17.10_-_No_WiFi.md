---
title: "HP ENVY x360 - 15-bq150na - Ubuntu 17.10 - No WiFi"
date: 2018-02-04
forum: Networking &amp; Wireless
---

### Post by wolflint on 2018-02-04
I just installed Ubuntu 17.10 on my new **HP ENVY x360 - 15-bq150na **but I can't find a way to get the WiFi to work. In the setting menu it just says no WiFi adaptor detected. 

I tried this [https://askubuntu.com/questions/677621/no-wireless-connection-on-hp-pavilion-x360-convertible#677634](https://askubuntu.com/questions/677621/no-wireless-connection-on-hp-pavilion-x360-convertible#677634) but it didn't work on my laptop, after a reboot I still had the same issue.

---

### Post by jeremy31 on 2018-02-04
*Thread moved to **Networking & Wireless**.*

See the wireless script link in my signature and post results

---

### Post by wolflint on 2018-02-09
Hi, I ran the script and the output file was empty. It just had the first line which indicated where the code output would be.

---

### Post by jeremy31 on 2018-02-09
What about results for ```
lspci -nnk | grep -iA3 net
```

---

### Post by wolflint on 2018-08-21
Sorry for the late reply but I gave up then xD
I bought a USB ethernet adapter now so this should be easier now.
Any way here is the pastebin: [http://paste.ubuntu.com/p/GQNHQB5w3F/](http://paste.ubuntu.com/p/GQNHQB5w3F/)
thanks for helping. I am trying with 18.04 now

---

