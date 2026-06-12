---
title: "Wireless not working anymore"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by omni504 on 2009-04-21
Let me first off start with what happened leading up to this, maybe it would help someone help me:

My laptop is T-1625 gateway, and it recently tried connecting to some network called "hpsetup" in which case the laptop locked itself up and kept doing so, until i managed to take the "auto" off that network right before it locked up again. 

Now my normal wireless doesnt work anymore, meaning i can connect to a network and everything, but when i try to go to a website it'd just say it cant find the page and maybe im not connected to the internet and such. i get a firefox error page load message. And i tried pinging google and everything, and that i would have no packets recieved all lost. Like im not connected to a network at all...
I went through the ubuntu built in help and went through the wireless troubleshooting, did everything there and still it was the same.

If anyone can help me out it would be much appreciated... Especially now that the 9.04 is due out soon =(.

---

### Post by halitech on 2009-04-21
try opening a terminal and post the results of```
sudo ifconfig
```

---

### Post by omni504 on 2009-04-21
Ok, well i can't really copy and paste and i dont currently have a flash drive or cd to copy and paste from my laptop to this one, so i'll just hand type the wlan0 output since thats the one i use...
{

wlan0        Link encap:Ethernet HWaddr 00:16:44:7d:6e:36
             UP BROADCAST MULTICAST MTU:1500 Metric:1
             RX packets:0 errors:0 dropped:0 overruns:0 frame:0
             TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:1000
             RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
}

This is not when im connected to anetwork however since i don't have access to a network at the moment. Did I need to go ahead and connect to network and then type ifconfig? Or is this fine?

---

### Post by ugriffin on 2009-04-21
Ok, I'm not sure if this might be the problem, but try:

```

sudo ufw disable

```

It might just be the firewall.

---

### Post by halitech on 2009-04-22
> **omni504 said:**
> Ok, well i can't really copy and paste and i dont currently have a flash drive or cd to copy and paste from my laptop to this one, so i'll just hand type the wlan0 output since thats the one i use...
{

wlan0        Link encap:Ethernet HWaddr 00:16:44:7d:6e:36
             UP BROADCAST MULTICAST MTU:1500 Metric:1
             RX packets:0 errors:0 dropped:0 overruns:0 frame:0
             TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:1000
             RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
}

This is not when im connected to anetwork however since i don't have access to a network at the moment. Did I need to go ahead and connect to network and then type ifconfig? Or is this fine?

mainly I just wanted to see if the card was still there which it is. Have you tried doing a scan for networks to see if it can locate any from the command line?

```
sudo iwlist scan wlan0
```I think thats the correct code.

---

### Post by omni504 on 2009-04-22
I have no problems scanning for networks or connecting to networks at all. Everything looks like it works fine, until i try to open up firefox and it automatically goes to google, but it gives me an error message and tells me to check my DNS settings and check to see if im connected to the internet.

---

### Post by halitech on 2009-04-22
ok, connect to a network and run the same command to see if you are actually getting an IP address. Also, check and make sure fire fox is not set to work offline

---

