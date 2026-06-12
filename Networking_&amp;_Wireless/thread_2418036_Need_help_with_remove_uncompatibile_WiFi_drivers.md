---
title: "Need help with remove uncompatibile WiFi drivers"
date: 2019-04-30
forum: Networking &amp; Wireless
---

### Post by xxxp771 on 2019-04-30
Hello everyone! :)


I have a problem with wifi driver, few days ago my computer showed me information that I don't have wifi card installed so i tried to install some drivers.
Unfortunetelly I installed difrent drivers than my computer required. (I use this commend)
sudo apt remove bcmwl-kernel-source && sudo apt install git dkms
git clone -b extended [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6


My Computer is acer Aspire 5 A515-52G
and wifi card is Intel 9560NGW
Ubuntu 18.04


The problem was the card was unpluged from motherboard so old drivers were good.
Can you please tell me how can I remove current drivers and restore proper drivers to my wifi card.


Best wishes

---

### Post by jeremy31 on 2019-04-30
Please see the wireless script link in my signature and post results.

---

### Post by xxxp771 on 2019-04-30
This is my wireless info

[http://paste.ubuntu.com/p/n7S2dQ7DYQ/](http://paste.ubuntu.com/p/n7S2dQ7DYQ/)

---

### Post by jeremy31 on 2019-04-30
You have some nasty error messages but you haven't set a country code, wifi power management is enabled, and your access point has TKIP enabled which may contribute to the errors, see chili555's post at [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
Then reboot and see if it is better, if not do
```
./wireless-info && cat wireless-info.txt | nc termbin.com 9999
```
Post URL with results

---

### Post by xxxp771 on 2019-04-30
I did what chili55 said and still have problem 

here is my result
[https://termbin.com/1nza](https://termbin.com/1nza)
[http://paste.ubuntu.com/p/D2z8SBxK3b/](http://paste.ubuntu.com/p/D2z8SBxK3b/)

is there any posibility to remove current drivers and install proper from intel side? [https://www.intel.pl/content/www/pl/pl/support/articles/000005511/network-and-i-o/wireless-networking.html](https://www.intel.pl/content/www/pl/pl/support/articles/000005511/network-and-i-o/wireless-networking.html)
I also would like to point out that I first installed drivers that do  not comply with my wifi card. how can I uninstal those?

---

### Post by jeremy31 on 2019-04-30
Your router info shows that TKIP is still enabled, but try this and reboot
```
echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlopt.conf
```

---

### Post by praseodym on 2019-04-30
```
sudo dkms remove rtlwifi-new/0.6 --all
sudo rm -r /usr/src/rtlwifi-new-0.6 
```
should do the job

---

### Post by jeremy31 on 2019-04-30
I forgot one thing, you might want to remove wicd as it might conflict with network manager if they both are running

---

### Post by xxxp771 on 2019-05-01
Thank you for your help.
I removed old drivers and wicd but still have probelm with WiFi 

Can you sugest me some drivers and kernel which work?
Also before I installed the wrong drivers, WiFi worked fine, juts wrong drivers messed up my system.

---

