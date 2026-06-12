---
title: "Packet loss using RTL8188CUS (0bda:8176)"
date: 2015-01-02
forum: Networking &amp; Wireless
---

### Post by dcomsa on 2015-01-02
Hi all,

I'm having this problem with an USB wifi dongle where it keeps dropping packets. I'm trying to use it on a Raspberry Pi but even on my laptop it has the same behavior. What's frustrating is that it works fine on Windows :(

```
daniel@daniel-laptop:~$ ping -I wlan1 192.168.0.1
PING 192.168.0.1 (192.168.0.1) from 192.168.0.13 wlan1: 56(84) bytes of data.
(...)
--- 192.168.0.1 ping statistics ---
101 packets transmitted, 86 received, 14% packet loss, time 100219ms
rtt min/avg/max/mdev = 1.496/18.456/200.986/49.394 ms

```

Note that on this laptop I have to wireless cards:
wlan0 - the built in adapter which works fine
wlan1 - the USB one that's having problems

I've been reading several posts and seen a script (user 'varunendra' - can I tag a user btw?) that gathers additional details from a system. Please find its output attached.

Any idea about what I could try?

Thanks and regards,
Daniel.

---

### Post by dcomsa on 2015-01-02
Looks like the script is the one from the sticky thread :)

---

### Post by chili555 on 2015-01-02
Wow; just wow...

It appears that you have two wireless devices and they are *BOTH* connected. And you say you are having trouble?? I wonder why.

If you do not wish to use the internal because you have given it a thorough troubleshooting and still can't get it working as expected, then I recommend you blacklist its driver and then see what happens with the USB.

---

### Post by dcomsa on 2015-01-03
Hi chili555,

Thanks for taking the time to reply. Just curious, why would it be a problem to have both connected? 

A few arguments from my side that it should not matter:
- the internal card works just fine while the USB one has some dropped packets (still works though) when both connected
- on windows both work just fine at the same time (simultaneously pinging the router using both adapters)
- on Raspberry Pi I have the same problem (dropped packets) and it's just this adapter
 
I'm using my laptop (which has the built in one) for troubleshooting purposes, hence the dual adapters, but in the end I would want to use the adapter on my RPi.

Cheers,
Daniel.

---

### Post by praseodym on 2015-01-03
Hi,

change the driver for the stick:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by dcomsa on 2015-01-03
Lovely, seems to be working :)

```
daniel@daniel-laptop:~$ ping -I wlan1 192.168.0.1
PING 192.168.0.1 (192.168.0.1) from 192.168.0.13 wlan1: 56(84) bytes of data.
(...)
--- 192.168.0.1 ping statistics ---
101 packets transmitted, 101 received, 0% packet loss, time 100140ms
rtt min/avg/max/mdev = 4.513/16.339/370.488/35.945 ms

```

Many thanks praseodym. Now I need to figure out how to compile it on RPi, but that's another story.

Cheers,
Daniel.

---

