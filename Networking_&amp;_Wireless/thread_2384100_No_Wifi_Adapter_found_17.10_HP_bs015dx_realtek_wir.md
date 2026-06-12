---
title: "No Wifi Adapter found 17.10 HP bs015dx realtek wireless adapter"
date: 2018-02-02
forum: Networking &amp; Wireless
---

### Post by daniel4128 on 2018-02-02
Hello, I recently installed Ubuntu 17.10 on my Hp bs015dx laptop (dual boot windows 10). My wifi and ethernet work perfectly on windows but not on  ubuntu. It says "no wifi adapter found" when i go to settings. I've included the wireless info text file I got from Terminal after running a certain command(I don't really remember what it is:o). I'm hoping someone can help me out with this. Thank you.

---

### Post by jeremy31 on 2018-02-02
Try
```
sudo apt-get install build-essential git dkms
git clone https://github.com/jeremyb31/rtl8723de.git
sudo dkms add ./rtl8723de
sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414 
```
Reboot and wifi should work

---

### Post by daniel4128 on 2018-02-07
Thank you so much. It worked just fine. You're the best.

---

