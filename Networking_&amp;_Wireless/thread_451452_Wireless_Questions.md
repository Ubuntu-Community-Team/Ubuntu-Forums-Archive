---
title: "Wireless Questions"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by Darkdelusions on 2007-05-22
I know that FF does not support WPA and static IP in the Network manager. However I was wondering if there are good programs out there that will allow this fucntionality. I recently bought a laptop and want to toss ubuntu on it however I share my laptop with my GF who is a computer novice So I need something that is simple and will work for her when she boots the pc

I have tried WI-Fi Radar and had no luck getting it to work. and I was unable to get wicd install

---

### Post by Praill on 2007-05-22
For the life of me, I dont know why wpa isnt supported out of the box. It may be in fiesty (i dunno), but its not in edgy.

Anyways, if it isnt already installed its simple:
```

sudo apt-get install wpasupplicant network-manager-gnome

```

```

gksudo gedit /etc/network/interfaces

```
comment out (put a # beside) all lines but the lines containing 'lo' information (usually the top two).

ctrl+alt+backspace to restart X. Re-login and you should have a working networking manager in the task bar that can configure wpa encrypted networks and is much much more functional and easy to use.

---

### Post by Darkdelusions on 2007-05-22
I apoligize I am running fiesty. WPA is supported out of the box however WPA and static is not.

---

### Post by Praill on 2007-05-22
Static IP? There HAS to be a way to do that in ubuntu. Im at work right now, i'll look into it when i get home.

---

### Post by thunderkyss on 2007-05-22
> **Praill said:**
> Static IP? There HAS to be a way to do that in ubuntu. Im at work right now, i'll look into it when i get home.

In manual configuration. that's how mine is set up.

---

### Post by Darkdelusions on 2007-05-22
If you go into network manager and try to Manually configure your networking you have the choice of wep or no encryption. I can use the stucking post at the top of the page however this will confuse my girlfriend. I was looking for an easy way to setup WPA with a static IP.

---

### Post by z-two on 2007-06-01
I have exactly the same problem. If i leave the wireless in "roaming mode" then it automatically asks me for the wpa key and works fine. But If i try to use the manual configuration (so that I can set up a static ip) WPA does not appear as an option, only WEP.

---

### Post by emperon on 2007-06-05
any solutions for WPA and static IP ?

---

