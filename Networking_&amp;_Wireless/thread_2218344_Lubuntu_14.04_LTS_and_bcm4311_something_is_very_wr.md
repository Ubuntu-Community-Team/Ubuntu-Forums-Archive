---
title: "Lubuntu 14.04 LTS and bcm4311 something is very wrong"
date: 2014-04-20
forum: Networking &amp; Wireless
---

### Post by googleorganico on 2014-04-20
I created a usb live persistent 4GB Lubuntu 14.04 with md5sum checked !

Something is very wrong with this 14.04 and bcm 4311, because with 13.10 it use to work only installing the linux-firmware-nonfree and edit the blacklist.conf and put a # before this sentence. But with this Lubuntu 14.04 i tryed all of this [http://paste.ubuntu.com/7292079/](http://paste.ubuntu.com/7292079/) and nothing put it my bcm 4311 On never . Thanks GOD iam experiment in a usb live persitent usb 4 Gb, other wise i..

I still working with it normally with Lubuntu 13.10 on HArd Disk, and with Lubuntu 13.10 on  usb stick Live persistent also!

---

### Post by wildmanne39 on 2014-04-20
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz)depending on the size of the file and it will be placed in your home folder. The wireless information will help to diagnose your wireless issue, the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the (wireless-info.txt, or wireless-info.txt.tar.gz) file as a zip file. 

If you do not have ethernet connection then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385).
Thanks

---

