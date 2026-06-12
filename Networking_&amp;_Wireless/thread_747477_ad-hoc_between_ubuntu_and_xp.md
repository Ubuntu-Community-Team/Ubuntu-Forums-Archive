---
title: "ad-hoc between ubuntu and xp"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by mintyuser on 2008-04-06
I used this page: [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc) to establish an ad-hoc network between my computers.
I have 2 computers:
[B]
1.[/B] A desktop computer that is connected to the internet via wired network.
**2.** A laptop computer with wifi.

I wish to establish a network between the computers. once it's working, i also want internet connection sharing. that's why ad-hoc network is probably the easiest way.
[U]
What I did so far is:[/U]
On computer 1 I did:
```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode ad-hoc
sudo ifconfig wlan0 192.168.0.1
sudo iwconfig wlan0 essid 'net8'
sudo iwconfig wlan0 channel 7
sudo ifconfig wlan0 up
```

after doing it, i opened the wireless network window on the second computer (xp) and i see the "net8" network in the list - but i can't connect!
so i changed the the ip of computer (2) to 192.168.0.2 and the ad-hoc channel to 7, also I created a new ad-hoc network with the same essid. but still, i can only see the network on the list but can't connect.

any ideas?

---

