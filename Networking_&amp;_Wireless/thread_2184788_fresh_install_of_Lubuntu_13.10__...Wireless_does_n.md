---
title: "fresh install of Lubuntu 13.10  ...Wireless does not work"
date: 2013-10-30
forum: Networking &amp; Wireless
---

### Post by sdep777 on 2013-10-30
fresh install of Lubuntu 13.10  ...Wireless does not work 

I cannot get wireless to work on this even though it shows its already installed in Synaptic Pkg. manager, only see the LAN connection


Thank you

Steve -

---

### Post by praseodym on 2013-10-30
Please show the terminal outputs of
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by sdep777 on 2013-10-30
what?

---

### Post by wildmanne39 on 2013-10-30
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

