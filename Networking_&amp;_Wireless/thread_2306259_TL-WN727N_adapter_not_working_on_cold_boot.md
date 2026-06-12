---
title: "TL-WN727N adapter not working on cold boot"
date: 2015-12-13
forum: Networking &amp; Wireless
---

### Post by dhamith on 2015-12-13
I'm on Ubuntu 15.10 and my wireless adapter is TL-WN727N. Problem with this adapter on ubuntu is: if I cold boot in to ubuntu, it wont recognize the adapter. To get the adapter to work, I have to boot into windows, restart and then boot into ubuntu. Also, when the adapter is working, the indicator light on it, is dimmed (on windows it flashes to indicate network usage) I didn't noticed any slowdowns though. Is there any way to get this thing work? It's really annoying to boot into windows and reboot to ubuntu every time I turn on my PC.

---

### Post by Hadaka on 2015-12-13
Hi, please go here..
[http://askubuntu.com/questions/577941/installing-the-driver-for-tp-link-tl-wn727n-on-ubuntu-14-04](http://askubuntu.com/questions/577941/installing-the-driver-for-tp-link-tl-wn727n-on-ubuntu-14-04)
read the instructions then post your wireless-info.txt file
so we can help you find a solution.
thanks.

---

### Post by dhamith on 2015-12-14
It Worked! Thanks!

I've tried linux drivers from TP-Link site couple of times and it didn't worked.

---

### Post by slickymaster on 2015-12-14
> **dhamith said:**
> It Worked! Thanks!

I've tried linux drivers from TP-Link site couple of times and it didn't worked.

being so, please mark the thread as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), so  other people searching the forums know that it provides a working solution for the problem.

---

### Post by Hadaka on 2015-12-14
Glad this worked for you.
 ```
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/porjo/mt7601.git 
cd mt7601/src
make
sudo make install
sudo mkdir -p /etc/Wireless/RT2870STA/
sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/
sudo modprobe mt7601Usta
```


and after every linux image update
 	

 	```
cd ~/mt7601/src
make clean
make
sudo make install
sudo modprobe mt7601Usta
```

---

