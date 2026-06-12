---
title: "wlan0 - idle - interface does not exist, cant connect to the internet"
date: 2014-05-30
forum: Networking &amp; Wireless
---

### Post by Juna on 2014-05-30
Hi,

I am using Ubuntu 14.04 LTS.
I recently installed macchanger, and followed instructions to use it:

```
ifconfig
sudo ifconfig wlan0 down
sudo macchanger -r wlan0
sudo ifconfig wlan0 up
```

the macchanger didnt work anyway, all of the mac addresses were the same.
After this i tried to open my internet browser and it did not work.

I checked the network connection properties and it says that wlan0 is idle. when i try to configure the connection it says that it does not exist.
When i put in 
```
ifconfig wlan0
```
in the reply it has 'UP BROADCAST RUNNING MULTICAST' and various other things i will post if needed (i am using another computer obviously so must type everything)

I have looked through the forums but the network manager seems to be different on this version of lubuntu, as in there isnt a box for 'wireless connections'. And other people seem to have responses in terminal saying wlan0 does not exist, but i only get this in a dialog box outside of terminal when i try to configure it, otherwise in terminal the reading displays like wlan0 is busy. I cant get my head around this.

Hope someone can help. Thanks

---

### Post by cariboo on 2014-06-01
Moved to Networking and Wireless.

---

