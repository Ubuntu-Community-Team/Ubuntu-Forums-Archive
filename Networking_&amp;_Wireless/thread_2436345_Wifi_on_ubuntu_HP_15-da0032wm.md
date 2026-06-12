---
title: "Wifi on ubuntu HP 15-da0032wm"
date: 2020-02-04
forum: Networking &amp; Wireless
---

### Post by steve60901 on 2020-02-04
I have tried every tutorial post I could find to try and get this working. The wireless adapter just will not show up. I'm also not positive if there's a realtek wireless adapter in it or an intel one altho i didn't know intel made wireless adapters... anyway the model number for the laptop is in the title. Using kubuntu 19.10 if anyone can help it would be much appreciated. I have wired connectivity but obviously thats not what you want with a laptop lol

---

### Post by CelticWarrior on 2020-02-04
Trying "every tutorial" without knowing the actual hardware is usually a recipe for disaster.

Please open the terminal and run ```
lspci -knn | grep Net -A3
```

then post it here.

---

### Post by steve60901 on 2020-02-04
lspci -knn | grep Net -A3

---

### Post by steve60901 on 2020-02-04
steve@steves-HP-Laptop:~$ lspci -knn | grep Net -A3
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821]
        DeviceName: WLAN
        Subsystem: Hewlett-Packard Company RTL8821CE 802.11ac PCIe Wireless Network Adapter [103c:831a]

---

### Post by steve60901 on 2020-02-04
I've already downloaded the newest rtlwifi and did the whole make and make install bit but no go.

---

### Post by jeremy31 on 2020-02-04
Moved to Networking,
Check results for
```
mokutil --sb-state
```
Secure Boot needs to be disabled, then in terminal try
```
sudo apt install rtl8821ce-dkms
```
Reboot

---

### Post by CelticWarrior on 2020-02-04
> **steve60901 said:**
> I've already downloaded the newest rtlwifi and did the whole make and make install bit but no go.

Bad move. The drivers are already either available in the repositories (19.10) or already packaged for earlier releases. Considering you have 19.10 then ```
sudo apt install rtl8821ce-dkms
``` (and disable Secure Boot in UEFI).

---

### Post by steve60901 on 2020-02-04
BINGO!! Thank you guys so much... i'll bet my sammiches it was that uefi boot junk... which in NONE of the tutorials did it say to turn that off... currently sending this reply over wifi

---

### Post by CelticWarrior on 2020-02-04
> **steve60901 said:**
> which in NONE of the tutorials did it say to turn that off... 

No surprise, at all :p

Most of those were probably written by people who disable it routinely even before installing Ubuntu, like I do.

---

