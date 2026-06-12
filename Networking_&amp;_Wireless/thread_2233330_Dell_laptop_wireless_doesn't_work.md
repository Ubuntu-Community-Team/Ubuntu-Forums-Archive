---
title: "Dell laptop wireless doesn't work"
date: 2014-07-07
forum: Networking &amp; Wireless
---

### Post by kickwin on 2014-07-07
I can't seem to get my wireless working. I would appreciate if you folks can help me with this. Here is output of some commands that you experts may want to take a look at:

iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.
```

lspci -vvnn | grep 14e4
```

02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
```

lsmod | grep -e b43 -e wl
```
b43                   356470  0 
bcma                   42043  1 b43
mac80211              545990  1 b43
cfg80211              409394  2 b43,mac80211
ssb                    51854  2 b43,b44
```

---

### Post by slooksterpsv on 2014-07-08
Awesome it's detecting it, what kind of dell laptop? Is the wireless turned on - e.g. some have switches on the front, some its a key press like Fn+F2, some there's nothing - so is it turned on? (Especially if there's a physical switch).

Xubuntu, what version? 13.10, 14.04, 12.04 and 32-bit or 64-bit?

---

### Post by kickwin on 2014-07-08
It is a Dell Inspiron 1300. The shortcut for turning on Wifi is Fn + F2 but pressing it doesn't do anything.

I installed Xubuntu 14.04 32-bit.

---

### Post by slooksterpsv on 2014-07-08
EDIT: If you can connect it via Ethernet and go to Ubuntu Software Center -> Edit - > Software Sources -> Additional Drivers 
and see if it's listed under there.

I hate doing this, but I think we need to go through this document:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

There's a lot of useful stuff. bcm43xx cards are notorious for random issues, hence the creation of that article. I'd try some of those, especially the bcm43 firmware area. If none of those work, let us know. You will need to connect via ethernet to try the steps. I feel like it's a driver issue.

---

### Post by kickwin on 2014-07-08
Ah. It was nice to get some community love at Ubuntu. Missed it for a long time. I just was so bored with a perfectly stable Crunchbang that didn't require tweaking for years as it was removed  from development (XFCE version). I am sure I will go back to being like that with Xubuntu but hopefully there are updates that keep me engaged. 

ANyway, this did the trick for me:

```
sudo apt-get update
If you have a **b43** card use the command 
sudo apt-get install firmware-b43-installer
```

I think I tried the "firmware-b43..." without update and it didn't work.

---

### Post by slooksterpsv on 2014-07-08
Awesome, if you're satisfied with the resolution, you can mark thread as solved, so if others are looking for a fix, they can find your thread and see it was solved somewhere. It's at the top under thread tools above your first post.

---

### Post by Bucky Ball on 2014-07-09
Posted in error.

---

### Post by Bucky Ball on 2014-07-09
> **kickwin said:**
> 
```
sudo apt-get update
sudo apt-get install firmware-b43-installer
```



... then reboot. Beat me to it. Exactly what I was about to post. Well done. Enjoy! ;)

---

