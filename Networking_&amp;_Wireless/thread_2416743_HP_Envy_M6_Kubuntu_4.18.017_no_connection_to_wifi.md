---
title: "HP Envy M6: Kubuntu 4.18.017 no connection to wifi"
date: 2019-04-14
forum: Networking &amp; Wireless
---

### Post by rzewrob on 2019-04-14
Hey there,

Ive been attempting fixes on Kubuntu for not being able to connect to a wireless connection. Have attempted to install drivers, clean install, and among a few other trouble shoots. though being new I still can not find the correct solution. Here is my PasteBin for the wifi script [http://paste.ubuntu.com/p/prb6Zt4VRv/](http://paste.ubuntu.com/p/prb6Zt4VRv/). Hopefully someone can lead me in the right direction!

---

### Post by pcfan1234 on 2019-04-16
Run 
sudo apt-get install bcmwl-kernel-source

---

### Post by rzewrob on 2019-04-22
Got back E: dpkg was interrupted, you must manually run 'sudo dpkg -- configure -a' to correct the problem. 
I also swore I installed the bcmwl kernel by using a flash drive initially but must have failed at that.


Attempted it again and got a successful install that tells me i have the kernel already installed

---

### Post by praseodym on 2019-04-22
Blacklist the native driver
```

echo 'blacklist b43' | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot and deactivate SecureBoot

---

### Post by rzewrob on 2019-04-22
Will attempt it later today. Will edit post if more issues arise. At the moment thank both of you for your assistance.

---

