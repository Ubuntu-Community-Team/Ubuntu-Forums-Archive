---
title: "wpa_supplicant wifi suddenly not working"
date: 2015-02-11
forum: Networking &amp; Wireless
---

### Post by Timothy_Penang_Ubu on 2015-02-11
Everything was working before.
Then, I made the dumb error of editing the binary file /sbin/wpa_supplicant with pico text editor.
and now it doesn't load at all and consequently, I don't have wifi support, wlan0 is also not found (this should be found right? I think I have the wifi card on eth2). eth2: IEEE 802.11 wifi card: BCM4321.

I tried downloading and compiling a new wpa_supplicant from their official site, but it seems that my ubuntu doesn't want to care about the replaced wpa_supplicant anymore. Like some bird kill abandoning her eggs after they were touched by men.

Help!

Thanks.

---

### Post by Hadaka on 2015-02-11
Hi, lets verifiy the correct driver.Please do and post..
```
lspci -n | grep 0280
```
thanks

---

### Post by Timothy_Penang_Ubu on 2015-02-11
$ lspci -n | grep 0280
05:00.0 0280: 14e4:4328 (rev 03)

Looks good?
btw: running wpa_supplicant gives error: Segmentation Fault

---

### Post by Hadaka on 2015-02-11
This probably wont work,but give it a try.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
sudo modprobe -rf b43
sudo modprobe b43
```

---

### Post by Timothy_Penang_Ubu on 2015-02-11
Nope, nothing changed.
I have a feeling the solution is focused on wpa_supplicant, because it is the only thing I changed before and after the problem. I foolishly used a text editor to modify the binary file wpa_supplicant to add the word "none", next to MSCHAPV2. And after that, the kernel doesn't run wpa_supplicant as it used to, even after I removed the word "none" - although, since I did all this using text editor, I'm not sure how seriously have I corrupted the binary file. That means, whatever the fix is, it must involve wpa_supplicant to be modified or recompiled or something.

But all being said, I could be wrong. Thanks for trying to help!

---

