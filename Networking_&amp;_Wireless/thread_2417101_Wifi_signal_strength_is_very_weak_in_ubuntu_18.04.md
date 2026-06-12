---
title: "Wifi signal strength is very weak in ubuntu 18.04"
date: 2019-04-20
forum: Networking &amp; Wireless
---

### Post by rafahfaria232 on 2019-04-20
Hello, 

I'm using HP laptop. I have previously faced wireless connection issues, no wifi issues in my system. Currently using ubuntu 18.04 LTS. I'm getting very low and weak signal in my laptop. While I'm close to the router I get moderate signal. I have tried all possible solution I could find. Installed few driver files from git, but none of these are actually working. rtl8723be  is my wireless driver. Looking forward to get an effective solution. Thank you.

---

### Post by jeremy31 on 2019-04-20
Please see the wireless script link in my signature and post results

---

### Post by rafahfaria232 on 2019-04-20
[http://paste.ubuntu.com/p/9BxKjzWF87/](http://paste.ubuntu.com/p/9BxKjzWF87/)

---

### Post by praseodym on 2019-04-20
> 
```
[/etc/modprobe.d/50-rtl8723be.conf]
options rtl8723be ant_sel=2
```

Try instead

```
echo 'options rtl8723be ant_sel=1' | sudo tee /etc/modprobe.d/50-rtl8723be.conf
```
Reboot

---

### Post by rafahfaria232 on 2019-04-21
> **praseodym said:**
> Try instead

```
echo 'options rtl8723be ant_sel=1' | sudo tee /etc/modprobe.d/50-rtl8723be.conf
```
Reboot

I've tried that previously, also tried it once again. Doesn't make any difference to the signal strength.

---

### Post by jeremy31 on 2019-04-21
You could remove the bottom panel from the laptop and switch the antenna wire to the other connector

---

### Post by rafahfaria232 on 2019-04-22
This finally solved my problem. Receiving higher range now. Thanks a lot!

---

### Post by rafahfaria232 on 2019-04-22
> **jeremy31 said:**
> You could remove the bottom panel from the laptop and switch the antenna wire to the other connector

[COLOR=#000000]This finally solved my problem. Receiving higher range now. Thanks a lot![/COLOR]

---

