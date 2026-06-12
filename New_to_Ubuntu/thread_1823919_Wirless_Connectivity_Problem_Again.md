---
title: "Wirless Connectivity Problem Again"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by kaine007 on 2011-08-12
I have tried everything in the book and still can not connect to my wireless internet via ubuntu. I formally used windows on the system and had no problems with connectivity until i changed the system to ubuntu.
I use a Dell Inspiron 6400 with Broadcom STA wireless card. I am able to connect to the internet via LAN but not wirelessly. I have had to reinstall the whole OS over and over again because anytime I install the bcmwl5 or 6 inf file i loose connectivity entirely. Both LAN or WLAN. 
Please Help

---

### Post by overdrank on 2011-08-12
Moved to Absolute Beginner Talk

---

### Post by bkratz on 2011-08-13
> **kaine007 said:**
> I have tried everything in the book and still can not connect to my wireless internet via ubuntu. I formally used windows on the system and had no problems with connectivity until i changed the system to ubuntu.
I use a Dell Inspiron 6400 with Broadcom STA wireless card. I am able to connect to the internet via LAN but not wirelessly. I have had to reinstall the whole OS over and over again because anytime I install the bcmwl5 or 6 inf file i loose connectivity entirely. Both LAN or WLAN. 
Please Help



You might want to copy/paste the outputs of the following terminal commands back here.

```
sudo lshw -C network
lspci -nn | grep 0280
iwconfig
rfkill list all
```

So we can see what card you have.

---

### Post by amjjawad on 2011-08-13
> **bkratz said:**
> You might want to copy/paste the outputs of the following terminal commands back here.

```
 sudo lshw -C network
```

```
 lspci -nn | grep 0280
```

```
 iwconfig
```

```
 rfkill list all
```

So we can see what card you have.

Run one command at a time and post the output of each command alone and please wrap up the text with CODE tags or just highlight the text and click on "#".

---

