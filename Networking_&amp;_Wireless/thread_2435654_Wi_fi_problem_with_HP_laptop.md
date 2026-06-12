---
title: "Wi fi problem with HP laptop"
date: 2020-01-23
forum: Networking &amp; Wireless
---

### Post by itgamer on 2020-01-23
I installed ubunty 18.04 and sence than can't connect to wi fi.I find some solutions to fix that from terminal but non of them worked for me.
Does anyone have simillar problem?

---

### Post by pcfan1234 on 2020-01-24
Do you see some networks and can't connect to a specific one or don't you see any networks?
Maybe an additional driver is needed. Show the output of ```
lspci -nnk
``` in this case.

---

### Post by itgamer on 2020-01-24
I see only No Wi-Fi Adapter found, but Bluetooth works.

---

### Post by slickymaster on 2020-01-24
Please have a read at this [sticky]("https://ubuntuforums.org/showthread.php?t=370108") and do what is requested there.

---

### Post by itgamer on 2020-01-24
How to post an image here? With that command I see list of drivers.

---

### Post by slickymaster on 2020-01-24
All you have to do is download and run the wireless info script, which will gather information to help diagnose your system. You can run it using this command in a terminal window:
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```
It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz". If you prefer, you can post the file directly to [pastebin]("http://pastebin.com/") yourself.

---

### Post by itgamer on 2020-01-24
Just do that but I still can't connect. Anyway thanks for help. I will ask some of my friends in IT to try to fix this. I try every solution I could found online

---

### Post by CelticWarrior on 2020-01-24
The script is intended to gather information about your hardware, something already requested and ignored. Without knowing your specific hardware it's impossible to help you and, of course, trying random advice that's likely not applicable to your hardware can only make things worse.

Good luck with your friends.

---

### Post by itgamer on 2020-01-24
Thanks, maybe solution is easy but I just did not found that one for my laptop

---

### Post by slickymaster on 2020-01-24
> **itgamer said:**
> Just do that but I still can't connect. Anyway thanks for help. I will ask some of my friends in IT to try to fix this. I try every solution I could found online

You haven't post the output you got from the script. You'll have to do that in order to get a diagnose to your problem.

---

