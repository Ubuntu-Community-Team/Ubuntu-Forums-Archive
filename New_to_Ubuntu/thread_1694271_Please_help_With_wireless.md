---
title: "Please help With wireless"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by vanquishedangel on 2011-02-24
I know this was prolly not the place but i am fairly new to linux, and I noticed that where i originally posted wasn't getting to many answers and some are years old with out replies. 
anyway i am needing help here

[http://ubuntuforums.org/showthread.php?p=10454028](http://ubuntuforums.org/showthread.php?p=10454028)

it is getting views, almost 200 in a week, but no answers and this laptop is running steller with maverick, just not the wireless.

I do appreciate your time to help.

---

### Post by arochester on 2011-02-24
Have you seen this? "WifiDocsDeviceCompaqW200" - [https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200)

It might be easier to get a **Linux compatible** wireless dongle from ebay...

---

### Post by vanquishedangel on 2011-02-24
> **arochester said:**
> Have you seen this? "WifiDocsDeviceCompaqW200" - [https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200)

It might be easier to get a **Linux compatible** wireless dongle from ebay...

I did follow that guide but it is very old. thank you though for the fast response. It would be easier i am sure, but i hate wasting money.

Actually I am sure this card and the driver are working flawlessly, I think it is a setting issue some where

---

### Post by vivek.pandey on 2011-02-26
sorry to ask this question as i am not good in reading very long stuffs. straight to the point. are you using a usb modem as you mentioned something related to your strange usb port?
one more thing are you sure you are not connected as the output of ifconfig you posted has your internet address 192.168.2.2 in it

---

### Post by vanquishedangel on 2011-04-06
> **vivek.pandey said:**
> sorry to ask this question as i am not good in reading very long stuffs. straight to the point. are you using a usb modem as you mentioned something related to your strange usb port?
one more thing are you sure you are not connected as the output of ifconfig you posted has your internet address 192.168.2.2 in it

Sorry it took me awhile to get beck on this, the problem was bad firmware and the thread is solved, 2 files need to be removed and then it works out of the box actually, once the firmware is downloaded and placed in the folder it needs to be, (/lib/firmware/your-kernel) and then a reboot will work, but you have to remove 2 files from /lib/firmware, agere_ap_fw.bin and agere_sta_fw.bin are both bad and can be put in the trash, there maybe an error about firmware missing when you restart again, but it will work great. I use LXDE on it now and it works there to.

The card is a w200 compaq wireless.

---

