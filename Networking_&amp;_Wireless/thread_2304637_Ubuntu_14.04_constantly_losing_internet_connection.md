---
title: "Ubuntu 14.04 constantly losing internet connection on WIFI"
date: 2015-11-28
forum: Networking &amp; Wireless
---

### Post by childintime on 2015-11-28
So I just installed Ubuntu 14.04.03 on my laptop and connected to Wifi using WPA2.

For some reason internet constantly disappears. For example I connect to it and then after 20 seconds to 15 minutes time period internet disappears even though I am still connected to the router. Then I press on the SSID in the network section on top and it reconnects and internet appears again (for 0.1 to 15 minutes or so). Again, I want to emphasize that when internet disappears it still shows that I am connected to that router.

Few things:

- I have Windows 8.1 laptop nearby which works perfectly, so I'm assuming it's not the router problem.
- I have Android phone connected which also works without issues.
- I don't have access to the router. But we had it reset, and it makes no difference.

I tried this but it made no difference: 

```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
```
sudo iwconfig wlan0 power off
```

Ifconfig (if it you need)

```
smth@compu:~/Downloads ifconfig
eth0      Link encap:Ethernet  HWaddr 74:d0:2b:d9:be:7f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:24887 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24887 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1987658 (1.9 MB)  TX bytes:1987658 (1.9 MB)


wlan0     Link encap:Ethernet  HWaddr 6c:71:d9:91:64:cd  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6e71:d9ff:fe91:64cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:669551 errors:0 dropped:0 overruns:0 frame:0
          TX packets:406962 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:869509276 (869.5 MB)  TX bytes:47029052 (47.0 MB)



```

P.s. I had this same issue when I was using Ubuntu 14.04.03 from Live USB.
Also note, before I installed this new Ubuntu, I was using same 14.04.03 before with (I think) 3.16 kernel and it was working perfectly. Not sure what changed in this new version.. However maybe I changed something wifi related in previous ubuntu I don't remember.

---

### Post by ajgreeny on 2015-11-28
What wireless adapter do you have?

The wireless-info-script will also help us figure out what's wrong.
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by childintime on 2015-11-28
I think it's Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01).
Kernel driver in use: ath9k

Here's script output:

Edit: internet is almost unusable, I need to reconnect every 10 seconds.\

Also note, before I installed this new Ubuntu, I was using same 14.04.03 before with (I think) 3.16 kernel and it was working perfectly. Not sure what changed in this new version.. However maybe I changed something wifi related in previous ubuntu I don't remember.

---

### Post by childintime on 2015-12-12
So sometimes it works like 30 mins straight, sometimes it does not work almost at all and i´m rebooting wifi every few seconds and it barely loads a single page.

This fresh ubuntu install is almost unusable for me, i wonder maybe it´s something wrong with my hardware..

- wifi not working correctly
- grub messed up
- disk errors on boot
- ubuntu randomly freezes for no reason
- applications sometimes shut down without any reason, and i cannot start them again. ¨ps -aux | grep appName¨ does not show it on the list, but i it does not start neither via terminal, nor via gui.
- sometimes apps do not show up in the search
- high I/O wait and cpu load after suspend.

And all that after fresh ubuntu install and installing some main software, like chrome, skype, thunderbird.

**EDIT: I think it was defective HDD. Got new SSD and everything works perfectly!**

---

