---
title: "Problem with WiFi on Ubuntu"
date: 2020-05-05
forum: Networking &amp; Wireless
---

### Post by asep2020 on 2020-05-05
[COLOR=#000000]Hi...[/COLOR]

i am new be on linux...

[COLOR=#000000]i have same problem, i am using ubuntu 20.04 lts new release and new lenovo ideapad 130-14ast. i can't use wifi.[/COLOR]
[COLOR=#000000]here i attachment the capture.[/COLOR]

[COLOR=#000000]Please help...thx[/COLOR]

---

### Post by chili555 on 2020-05-05
Your terminal output clearly says dkms not found. With a working internet connection by ethernet, tethering or whatever means possible, please do:

```
sudo apt install dkms
```

Then try again.

---

### Post by xxteraxx on 2020-05-05
ubuntu also has a package for rtl8821ce just do

```
sudo apt install rtl8821ce-dkms
```

---

