---
title: "asus SonicMaster : no adapteur"
date: 2018-07-12
forum: Networking &amp; Wireless
---

### Post by antooine42 on 2018-07-12
Hello everyone, I have the "no wifi adapteur found" problem, on an ubuntu 18.04 fresh install.
It's an "asus sonicmaster" laptop.

Here is the script output : [https://pastebin.com/b5UYBynq](https://pastebin.com/b5UYBynq)


Thank you for your help !

---

### Post by antooine42 on 2018-07-12
solved using this link : [https://askubuntu.com/questions/377050/how-do-i-get-mediatek-mt7630e-802-11bgn-wi-fi-adapter-working](https://askubuntu.com/questions/377050/how-do-i-get-mediatek-mt7630e-802-11bgn-wi-fi-adapter-working)


```
sudo apt-get install git dkms build-essential
git clone [https://github.com/neurobin/MT7630E.git](https://github.com/neurobin/MT7630E.git)
cd MT7630E/
sudo make dkms
```

---

### Post by praseodym on 2018-07-12
Great. Please use thread tools to mark it "SOLVED"

---

