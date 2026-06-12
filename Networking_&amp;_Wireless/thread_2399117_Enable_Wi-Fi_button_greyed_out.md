---
title: "Enable Wi-Fi button greyed out"
date: 2018-08-22
forum: Networking &amp; Wireless
---

### Post by gorgoilcane on 2018-08-22
Basically I can't click it. I tried everything I found online, but it didn't apply and I don't understand ubuntu
please help :icon_frown:

version: Ubuntu 14.04.5 LTS

---

### Post by Yellow Pasque on 2018-08-22
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by gorgoilcane on 2018-08-22
> **Temüjin said:**
> [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)


[COLOR=#000000]Here is the wireless-info.txt. Sorry [/COLOR]i'm at a loss

---

### Post by Yellow Pasque on 2018-08-22
Is there a wireless key/LED on your keyboard? I am not a wireless expert, but I do notice this:
```
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

So maybe try pressing the wireless key or unblocking with:
```
sudo rfkill unblock all
```
See if the LED changes color.

---

### Post by wildmanne39 on 2018-08-22
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by praseodym on 2018-08-22
What kind of computer is it? Dell?

---

### Post by gorgoilcane on 2018-08-22
> **Temüjin said:**
> Is there a wireless key/LED on your keyboard? I am not a wireless expert, but I do notice this:
```
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

So maybe try pressing the wireless key or unblocking with:
```
sudo rfkill unblock all
```
See if the LED changes color.


the code 'sudo rfkill unblock all' only opened my bluetooth. it didn't change anything else. The wifi led on my keyboard it's still off

---

### Post by gorgoilcane on 2018-08-22
> **praseodym said:**
> What kind of computer is it? Dell?

Yes, exactly, it's a Dell latitude e6410

---

### Post by Yellow Pasque on 2018-08-22
Make sure you didn't bump this switch: [http://thenextcorner.net/wireless-switch-dell-latitude-e6410/](http://thenextcorner.net/wireless-switch-dell-latitude-e6410/)

---

### Post by gorgoilcane on 2018-08-22
> **Temüjin said:**
> Make sure you didn't bump this switch: [http://thenextcorner.net/wireless-switch-dell-latitude-e6410/](http://thenextcorner.net/wireless-switch-dell-latitude-e6410/)


that's it, it worked! thank you so much, I had no idea that switch existed  

thanks to everyone

---

