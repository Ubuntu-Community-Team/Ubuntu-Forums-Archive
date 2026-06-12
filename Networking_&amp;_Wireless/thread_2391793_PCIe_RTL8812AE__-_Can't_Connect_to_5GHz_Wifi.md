---
title: "PCIe RTL8812AE  - Can't Connect to 5GHz Wifi"
date: 2018-05-13
forum: Networking &amp; Wireless
---

### Post by cowmoo32 on 2018-05-13
I've dug around and this seems to be a fairly common issue, but the  answers I've found haven't worked for me.  I tried the solution posted  here -  [https://ubuntuforums.org/showthread.php?t=2368840&p=13677732#post13677732](https://ubuntuforums.org/showthread.php?t=2368840&p=13677732#post13677732)  - but haven't seen any change.  Output of the wifi script in the sticky  is here - [https://pastebin.com/wQZr1w1f](https://pastebin.com/wQZr1w1f)

Looking at lsmod is interesting;  I think it's loading the wrong driver.  It's loading rtl88**21**ae, not rtl88**12**ae

```
##### lsmod #############################

rtl8821ae             229376  0
btcoexist             167936  1 rtl8821ae
rtl_pci                28672  1 rtl8821ae
rtlwifi                98304  3 rtl_pci,btcoexist,rtl8821ae
mac80211              774144  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              602112  2 mac80211,rtlwifi
mxm_wmi                16384  0
wmi                    16384  1 mxm_wm
```[URL="https://ubuntuforums.org/showthread.php?t=2368840&p=13677732#post13677732"]

[/URL]I just pulled the latest drivers from the rtlwifi github -  [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new) and get an error when trying to  load the correct driver for my card

```
sudo modprobe -r rtl8812ae
modprobe: FATAL: Module rtl8812ae not found.
```

---

