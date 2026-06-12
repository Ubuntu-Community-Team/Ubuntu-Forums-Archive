---
title: "help! Wi-fi Networks Device not ready [beginner]"
date: 2018-04-14
forum: Networking &amp; Wireless
---

### Post by yunxiaoli on 2018-04-14
I installed ubutu16.04 on my HP Omen 15-ce007 laptop today. Yet I cannot see any wireless networks. I followed the solution posted in this thread [https://askubuntu.com/questions/926364/how-to-make-my-pci-wifi-card-rtl8822-working-on-ubuntu/988975](https://askubuntu.com/questions/926364/how-to-make-my-pci-wifi-card-rtl8822-working-on-ubuntu/988975) 
then there came "Wi-fi Networks Device not ready" when clicking the network icon.
Thanks to ajgreeny, I could post necessary wifi-info below. It exceeds the 19.5kb size limit so i wrapped it in an archive. Sorry if it seems messy somehow.
[ATTACH]279289[/ATTACH]

---

### Post by praseodym on 2018-04-14
Installation:

```
sudo apt-get install git build-essential dkms linux-headers-$(uname -r)
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp /usr/src/rtlwifi-new-0.6/firmware/rtlwifi/* /lib/firmware/rtlwifi/ 
```
Reboot. For Bluetooth

```
git clone https://github.com/jeremyb31/bluetooth-4.4.git
sudo dkms add ./bluetooth-4.4
sudo dkms install bluetooth-4.4/0.1
```

---

### Post by yunxiaoli on 2018-04-14
Thank you for your prompt help! Just now I realized when I followed solution in the thread [https://askubuntu.com/questions/9263...-ubuntu/988975]("https://askubuntu.com/questions/926364/how-to-make-my-pci-wifi-card-rtl8822-working-on-ubuntu/988975") I made a reeeeally noob mistake and after fixing that Wi-fi works well.
Thanks again! I'm marking this as solved.

---

