---
title: "Can't find my Home Wireless"
date: 2015-01-22
forum: Networking &amp; Wireless
---

### Post by goncalo2 on 2015-01-22
Hello, so i just installed ubuntu 14.04.1 LTS in my desktop, so, i'm using dual boot, i also have windows 8.1 installed.

The problem is that i can't find my home wireless, i can find my neighbours wireless but i can't find mine. Can anyone help please? 
I really want to use ubuntu but i can't go like this.


Thank you for your time.

---

### Post by jeremy31 on 2015-01-23
check ```
iw reg get
``` to see if it matches your country code.  You can look at /usr/share/zoneinfo/zone.tab to find your country code if it is wrong and use the command ```
sudo iw reg set XX
```
Replace XX with the correct code and use capital letters

---

### Post by goncalo2 on 2015-01-23
Hello, thank you for your answer, i type the 1st code on the terminal this is what shows up:

```
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


```


I also typed the 2nd code on terminal but nothing happened. Please someone help me.

---

### Post by pfeiffep on 2015-01-23
> **goncalo2 said:**
> Hello, so i just installed ubuntu 14.04.1 LTS in my desktop, so, i'm using dual boot, i also have windows 8.1 installed.

The problem is that i can't find my home wireless, i can find my neighbours wireless but i can't find mine. Can anyone help please? 
I really want to use ubuntu but i can't go like this.

Thank you for your time.Is it possible that you configured your wireless router to NOT display it's name while using Windows 8? I have my router thusly configured and I must type the name into any device that I wish to connect.

---

### Post by jeremy31 on 2015-01-23
Reboot and run this in terminal, and attach the resulting wireless-info.txt
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```

---

