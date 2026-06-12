---
title: "Wifi Password Error"
date: 2021-02-04
forum: Networking &amp; Wireless
---

### Post by luke-leia on 2021-02-04
My ubuntu can find my wifi SSID but can not recognize my wifi password.
The interesting thing is that when I try to connect to Hot Spot from my mobile phone, ubuntu successfully recognize the password of hot-spot

In Ubuntu help, the recommendation is saying "Try the hex or ASCII pass key"
I can not understand this recommendation.

This is my first time to use Ubuntu.

Ubuntu 20.04.2 LTS
On my MacBook touch-bar 13" model.

Is there anyone to guide me to solve this problem?

---

### Post by praseodym on 2021-02-07
Do you have special characters in your password and/or ESSID? Does this show an output?

```
cat /etc/wpa_supplicant/wpa_supplicant.conf 
```

These characters are allowed

```
a-z A-Z 0-9 ! " # $ % & '( ) * + , - . / : ; < = > ? @ [ \ ] ^ _ ` { | } ~
```

---

