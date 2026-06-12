---
title: "Wireless internet not getting IP address?"
date: 2013-09-07
forum: Networking &amp; Wireless
---

### Post by panthraxnation on 2013-09-07
I recently changed the security on my router from WEP encryption to WPA-PSK. I can connect to the internet just fine on my Windows machines, my Android phones, and my Apple iPad, but Kubuntu will not gain an IP address. In Network Manager I can see under "Connection Status" where it goes through the steps to connect (configuring, etc) but it hangs at "obtaining network address" and under IP Address it shows "None".  Before I changed the security, I was on WEP encryption. Kubuntu would connect to it, but within a minute or two the connection would drop and it would take about five minutes before the connection ever picked up again, only to drop out another 1-2 minutes later.  Can somebody help please? Thanks a lot.

---

### Post by wildmanne39 on 2013-09-07
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

