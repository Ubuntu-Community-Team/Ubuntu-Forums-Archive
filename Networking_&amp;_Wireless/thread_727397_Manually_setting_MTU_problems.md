---
title: "Manually setting MTU problems"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by caljohnsmith on 2008-03-17
I followed the directions in this thread for manually setting the MTU for my wireless card:
[http://ubuntuforums.org/showthread.php?t=82093](http://ubuntuforums.org/showthread.php?t=82093)

I opened up /etc/network/interfaces, and added a line with "mtu 1492" as shown below:
------------------------------------------------------
# The primary network interface

iface wlan0 inet static
address 192.168.1.23
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid John's Home WLAN
mtu 1492

auto lo
iface lo inet loopback

auto wlan0
-----------------------------------------------------
I then did:
sudo ifdown wlan0
sudo ifup wlan0
And it returned an error:
SIOCSIFMTU: Invalid argument
Failed to bring up wlan0.

Also, if I do the command "sudo ifconfig wlan0 mtu 1492", it also returns the same error "SIOCSIFMTU: Invalid argument". So what am I doing wrong? How can I change my MTU permanently to 1492 instead of the default 1500 for my wireless card? Thanks for any help!

---

### Post by caljohnsmith on 2008-03-17
I've done more research and think it might have to do with my wireless card driver. As a long shot, is there any way I can modify my wireless card driver, i.e. the ".inf" file, to make 1492 as my default MTU? (Assuming of course I reinstall it).

---

### Post by caljohnsmith on 2008-03-25
Unfortunately, I'm still stuck with the same problem. 

Does anyone know how 1500 is chosen as the default MTU? Is this determined by the wireless card driver or is it a function of the Ubuntu OS? If it is a function of Ubuntu, where is located? It would sure help me trying to fix this problem if someone could possibly give me some troubleshooting tips.

Thanks for ANY help. :confused:

---

