---
title: "Intel Wireless 7265, iwlwifi iwlmvm poor performance sorta fix and notes"
date: 2016-05-29
forum: Networking &amp; Wireless
---

### Post by Ben_Maddocks on 2016-05-29
ISSUES and sum basic notes;
So my intel 7265D card on Ubuntu 14-16 on ASUS Q552 laptop, has had poor network performance on certain AP's and horrible signal quality issues. The iwlwifi backports not only didnt help solve any of the problems but it also broke all regulatory domain stuff. Ive tried all the different kernel versions, from 3.19 to 4.16. Many different firmwares as well. I just recently read that iwlwifi-7265D-17.ucode (CORE14) is the official firmware version for intel 7265D and all bug fixes will be included in future releases of that version. Even tho the newer drivers and firmware will work this is the one that should be used. Ive edited /etc/modprobe.d/iwlwifi.conf | iwlmvm.conf putting power to max and even disabling 802.11n none helped (disabling 802.11n helped a little)
A FIX! sorta;
So and this is gonna read backwards so ill reiterate. If Im running ON battery it works great! but I plug it in and signal goes to crap and no surfing (or very little) then disconnect and constantly asks for password again. I assume there sum sorta noise being produced by the PSU (probly on ground) but im hoping there might be a logical other reason. I know i have had to turn off usb autosuspend and other power management for wireless cards in the past, is there anything like that, that may explain this issue and solution? Anybody know what if any changes happen to the 7265D when switched to battery? TX/RX limits changing (even if specified not to in /etc/modprobe.d) and if so how i can make them happen when plugged into AC. 
Thank you and also Im fairly new to forums I hope I didnt do anything incorrectly.

---

