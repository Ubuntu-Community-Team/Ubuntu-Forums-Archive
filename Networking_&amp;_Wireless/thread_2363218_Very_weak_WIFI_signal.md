---
title: "Very weak WIFI signal"
date: 2017-06-07
forum: Networking &amp; Wireless
---

### Post by dsycho on 2017-06-07
Hey,
I'm a newbie in Ubuntu and I can't solve this problem.
At first I couldn't connect to my WiFi network, but I were capable of solving the problem by reading some posts at the forum.
But now my problem is different, my WiFi signal is very weak even when I am near the router (2 steps away).
I uninstalled windows 10 from my PC, but when I were using it the WiFi signal was fine.
If someone could help me I appreciate.
Thanks :)

---

### Post by LastDino on 2017-06-07
Ubuntu version? What steps did you take to get WiFi connected? What is your wifi chip and driver?

If you can shed some light there, people might have something to go on.

---

### Post by dsycho on 2017-06-07
I have Ubuntu 16.04 LTS.
Through the terminal I discovered my WiFi adapter is MT7630e, then I installed a driver for this model through this site [https://community.linuxmint.com/tutorial/view/1796](https://community.linuxmint.com/tutorial/view/1796)

---

### Post by wildmanne39 on 2017-06-07
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by dsycho on 2017-06-08
Is it this link?

[http://paste.ubuntu.com/24809732/](http://paste.ubuntu.com/24809732/)

---

### Post by wildmanne39 on 2017-06-08
Please do:
```
sudo apt purge bcmwl-kernel-source
```
Then:
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Check the settings in your router. WPA2-AES (CCMP) is best, not WPA and WPA2 mixed mode and do not use TKIP. 

Next, if your router can use N speeds, you will probably have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. You also should set a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Please set your settings in network manager to match the screenshots.

We need to set your country code:
```
sudo iw reg set PT
```
```
sudo sed -i 's/^REG.*=$/&PT/' /etc/default/crda
```

Your wifi signal is not weak.
Reboot

---

