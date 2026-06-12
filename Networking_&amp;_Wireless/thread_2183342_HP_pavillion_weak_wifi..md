---
title: "HP pavillion weak wifi."
date: 2013-10-24
forum: Networking &amp; Wireless
---

### Post by brianleppez on 2013-10-24
Hey all,

I recently installed Ubuntu on my HP laptop, but I get very weak wifi from it. When running Windows 8, I have full bars but with Ubuntu I only get 2 bars, sometimes 1 and after 10 minutes or so it disconnects and it connects again. If I get closer to the router I get better signal but my room is not even 50 feet from the router. 

Any tips on how to make this work?

I am new at Ubuntu.

---

### Post by wildmanne39 on 2013-10-24
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by brianleppez on 2013-10-24
Thank you for the reply, 

Here is the file.

---

### Post by wildmanne39 on 2013-10-24
Please do:
```
sudo apt-get purge --remove bcmwl-kernel-source
```
Then:
```
echo "blacklist iwlwifi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Change the channel in the router to 1 or 11 also set encryption to just wpa2 AES, and ```
disabling HT as WMM/QoS is not supported by the AP
```change that to enabled.
Reboot

---

