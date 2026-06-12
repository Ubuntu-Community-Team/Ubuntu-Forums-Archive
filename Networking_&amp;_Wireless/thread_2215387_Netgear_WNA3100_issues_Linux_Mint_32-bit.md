---
title: "Netgear WNA3100 issues Linux Mint 32-bit"
date: 2014-04-06
forum: Networking &amp; Wireless
---

### Post by Lprchn on 2014-04-06
Trying to get my wireless adapter to work on my desktop. Currently running Linux Mint 16 32-bit.

```
lprchn-pc@Lprchn ~ $ dmesg | grep ndis
lprchn-pc@Lprchn ~ $ 


```
```
lprchn-pc@Lprchn ~ $ sudo modprobe ndiswrapper
[sudo] password for lprchn-pc: 
FATAL: Module ndiswrapper not found.


```
```
lprchn-pc@Lprchn ~ $ ndiswrapper -l
bcmwlhigh5 : driver installed
    device (0846:9020) present


```

Thanks!

---

### Post by chili555 on 2014-04-06
Well, I was really hoping your thread would be on the Mint forum, but if the moderators don't catch us, let's try it here. With a working wired ethernet connection, do:```
sudo apt-get install ndiswrapper-dkms
sudo modprobe ndiswrapper
```If that doesn't solve it, we will use a bigger hammer.

---

### Post by Lprchn on 2014-04-06
Snap, wasn't aware there was a Mint forum. Hopefully they just move it and not delete it.

```
DKMS: install completed.
lprchn-pc@Lprchn ~ $ 


```
Done, then:

```
lprchn-pc@Lprchn ~ $ sudo modprobe ndiswrapper
lprchn-pc@Lprchn ~ $ 


```

---

### Post by chili555 on 2014-04-06
Alright! Now ndiswrapper loaded cleanly. What about:```
dmesg | grep ndis
iwconfig
```

---

### Post by Lprchn on 2014-04-06
```
lprchn-pc@Lprchn ~ $ dmesg | grep ndis
[21470.600921] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[21471.014366] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[21471.620463] usbcore: registered new interface driver ndiswrapper
lprchn-pc@Lprchn ~ $ iwconfig
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.


```

---

### Post by chili555 on 2014-04-06
I see nothing wrong there! Can you click the Network Manager icon, see your network and connect? Does it scan?```
sudo iwlist wlan0 scan
```We needn't see the whole list; just tell us if you get scan results or, if not, what the message is.

Generally, if it scans, it connects.

---

### Post by Lprchn on 2014-04-06
Restarted computer and did a little work in networking and the wireless is up and running! Thanks again Chili :)

Now, the last time it worked, the very next day it decided not to connect. So, I'll let you know if it decides to follow the same path. 

Thanks again man.

---

### Post by chili555 on 2014-04-06
Glad it's working. By the way, next time please check here: [http://forums.linuxmint.com/](http://forums.linuxmint.com/) I regularly post there, as well.

---

### Post by Lprchn on 2014-04-06
Will do, thanks!

---

### Post by fum on 2014-04-18
Chili555 I've been having issues with my WN3100 adapter as well. I noticed you come up in countless threads that I've searched up about the matter. Based on your knowledge would I be able to connect to WPA2? I can connect to WEP but my speed takes a huge toll and without encryption is just a no go since I live in an apartment building. I didn't think I should post a new thread. Thanks

---

### Post by chili555 on 2014-04-18
> I noticed you come up in countless threads that I've searched up about the matter. I need to get a new hobby or at least a life!

Which driver are you using?```
ndiswrapper -l
```What do the logs have to say about it?```
dmesg | grep ndis
```When we derive the answer, I will answer on askubuntu, too, so the searchers can see it.

---

### Post by fum on 2014-04-18
Delete

---

### Post by fum on 2014-04-18
> **chili555 said:**
> I need to get a new hobby or at least a life!

Which driver are you using?```
ndiswrapper -l
```What do the logs have to say about it?```
dmesg | grep ndis
```When we derive the answer, I will answer on askubuntu, too, so the searchers can see it.

I decided to make a thread due to the fact that his thread is labeled as SOLVED. [http://ubuntuforums.org/showthread.php?t=2217878&p=12992716#post12992716](http://ubuntuforums.org/showthread.php?t=2217878&p=12992716#post12992716)

---

