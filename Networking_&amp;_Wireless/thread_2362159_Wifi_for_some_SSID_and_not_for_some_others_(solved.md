---
title: "Wifi for some SSID and not for some others (solved)"
date: 2017-05-24
forum: Networking &amp; Wireless
---

### Post by melT4 on 2017-05-24
Hi,
Strange problem. I'm currently using wifi at home, however I'm unable to connect at work (I also experimented trouble with another public network). In fact, it connect, but it never resolve DNS. I recently upgrade to 16.04, hoping solving my problem but it doesn't. I dist-upgraded, and if possible, would like to avoid to do a clean re-install only for this issue.

I attached 2 files obtained from the same computer, both connected to "chum-sansfil".

wireless-info_nowifi : from my Ubuntu 16.04

wireless-info-live_working : from live-USB 16.04

working SSID is "lemien" and those not working is "ile-sans-fil" and "camp musical".

Thanks if someone could help me!
Mel

---

### Post by wildmanne39 on 2017-05-24
Before we even start, do you have access the routers? the signal and link quality is to low to connect to them and I do not believe in all the networks listed that I saw all the ones you want to connect too.

Lets keep this simple post the output just from the installed ubuntu version, and please use spacing to keep your post readable.

---

### Post by melT4 on 2017-05-24
No, I don't have access to routers, they are public network. I was connected to "chum-sans-fil". Only "ile-sans-fil" is also accessible. Other ones are from an other location.

---

### Post by wildmanne39 on 2017-05-24
This will help but with so many networks there is only so much we can do, please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Then:
```
sudo dpkg-reconfigure resolvconf
```
Then answer 'Yes' to the "Prepare /etc/resolv.conf for dynamic updates?" question and 'No' to the one about temporarily appending your existing config to the dynamic one, the second question I am almost positive has been removed in the later releases so if it is not their do not worry about it. 

Reboot and it should connect, both of the networks you want to connect to have the same signal strength and is on the same channel so it is probably going to jump back and forth between the two networks.

---

### Post by melT4 on 2017-05-25
wow, perfect is working! 
Thanks so much!
PS It effectively doesn't have a second question.

---

### Post by wildmanne39 on 2017-05-25
Thanks for confirming the 2nd question for me, I was pretty sure it had been dropped.

Glad it is working and Enjoy!

---

