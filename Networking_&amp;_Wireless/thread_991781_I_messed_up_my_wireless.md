---
title: "I messed up my wireless"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by cornish12 on 2008-11-24
Hi

I am using 8.10 and I had my wireless on my laptop working fine using WPA. I tried to get my webcam working by following a thread on this forum and had no luck with the webcam and it has also killed my wireless. i can connect when I disable the wireless setting but anything else WPA, WEP does not work. It does not connect and asks for my passpharase which I have repeatedly given. The only thing I did on the other thread was enter this at the terminal.

sudo apt-get install linux-backports-modules-$(uname -r)

on this thread SOLVED] Webcam driver update for Ubuntu-8.10  

The thread says just to uninstall if it does not work but I am new to ubuntu and I don't now how to do this.

Please help.

---

### Post by night_fox on 2008-11-24
```
sudo apt-get remove linux-backports-modules-$(uname -r)
```

---

### Post by cornish12 on 2008-11-24
That seems to have sorted it. Thanks.

---

