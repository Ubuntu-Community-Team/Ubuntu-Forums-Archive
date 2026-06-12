---
title: "Can't connect to specific wifi, has worked before (Ubuntu 16.04)"
date: 2017-06-11
forum: Networking &amp; Wireless
---

### Post by Klaster on 2017-06-11
Hey folks,

I'm having troubles connecting to my home wifi. It has worked before. Wired connection works like a charm. 

I have also connected to other wifis since the problem occurred. However, I experienced weird problems, as my connection with another wifi was very slow and slowed down the whole wifi for others as well (so slow that it was basically not usable).

I followed the instructions given here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) 

The output: [https://paste.ubuntu.com/24831487/](https://paste.ubuntu.com/24831487/) 

Thanks!
Jakob

---

### Post by Klaster on 2017-06-13
Anyone able to check on this? :???:

---

### Post by Hadaka on 2017-06-13
Hi, from a working wired connection, please COPY and paste
one line at a time..
```
sudo apt-get update
sudo apt-get dist-upgrde
sudo apt-get autoremove
sudo apt-get autoclean
```
then do..
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
sudo iw reg set DE
sudo sed -i 's/=.*/=DE/' /etc/default/crda
```
Next..access your router and configure as wpa2 ccmp aes...NO tkip
```
#'Baumhaus'  Group Cipher : TKIP  Pairwise Ciphers (1) : TKIP
```
If you are stil having issues after doing the above, please post a New
WIRELESS INFO DIAGNOSTIC REPORT.
Thanks

---

### Post by Klaster on 2017-06-18
Hi Hadaka,

I'm typing this while connected to the Wifi again. it works indeed, thanks a lot! I'll mark this solved. 

Thanks again!
Jakob

---

### Post by Hadaka on 2017-06-18
Glad that worked for you !
Thank you for marking your thread solved.

---

### Post by massoudestaki on 2017-12-15
Hi Hadaka,

I have similar problem. My laptop which I've setup Ubuntu 16.04 on it recently, connects to my home wifi, but not to the office. I've followed your instructions but still the same problem. 
The linux is installed along with a Windows 10 on the machine. The windows connects to the office wifi, however the Linux doesn't . 
Should I check anything else ?

---

