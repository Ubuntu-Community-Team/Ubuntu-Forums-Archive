---
title: "no wireless on lenovo s10-3, atheros ar9285, ubuntu 14.04 lts"
date: 2014-11-17
forum: Networking &amp; Wireless
---

### Post by Bernd_Finger on 2014-11-17
Hi,
just having installed 14.04 LTS on my old netbook, I'm trying for 2 hours now to get the wireless network up. Everything looks fine, I don't see any errors in dmesg, but the wiress network selection is grayed out. Ethernet works fine.

I tried already the tweak

echo "options ath9k nohwcrypt=1" | sudo tee  /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9kbut this does not help.

Any clues how to reanimate wireless are very welcome :-)
cheers,
   Bernd

---

### Post by jeremy31 on 2014-11-17
> **Bernd_Finger said:**
> Hi,
just having installed 14.04 LTS on my old netbook, I'm trying for 2 hours now to get the wireless network up. Everything looks fine, I don't see any errors in dmesg, but the wiress network selection is grayed out. Ethernet works fine.

I tried already the tweak

echo "options ath9k nohwcrypt=1" | sudo tee  /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9kbut this does not help.

Any clues how to reanimate wireless are very welcome :-)
cheers,
   Bernd

To make it quicker, could you follow the instructions in the sticky post "Before posting in networking and wireless" to run the wireless script and post results

---

### Post by Bernd_Finger on 2014-11-18
sorry, yes, should have read this before!

Nevertheless, I found the root cause of the problem. It seemed to be some settings on the internal wireless. I had to reinstall windows, apply the lenovo energy management tools and then I could active the wireless using the softkeys ... :-/ Now I'm doing my second try with ubuntu.

---

