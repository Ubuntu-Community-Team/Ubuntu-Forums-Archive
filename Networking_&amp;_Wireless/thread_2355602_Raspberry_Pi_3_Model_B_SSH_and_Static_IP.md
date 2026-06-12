---
title: "Raspberry Pi 3 Model B: SSH and Static IP?"
date: 2017-03-14
forum: Networking &amp; Wireless
---

### Post by awesomedude on 2017-03-14
I've done a fresh install of Ubuntu MATE onto my Raspberry Pi 3 Model B and went through the initial setup. I'm connected to my Home Network through WiFi and I do have access to the internet (using auto IP). However, I cannot seem to use SSH to connect to the Raspberry Pi. Here's the output of ifconfig:
```

enxb827ebcec5a1 Link encap:Ethernet  HWaddr b8:27:eb:ce:c5:a1
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1540 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:114633 (114.6 KB)  TX bytes:114633 (114.6 KB)


wlan0     Link encap:Ethernet  HWaddr b8:27:eb:9b:90:f4  
          inet addr:192.168.1.53  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:1 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60 (60.0 B)  TX bytes:0 (0.0 B)

```

I'm also trying to setup a local static IP address, but when I modified the /etc/network/interfaces file I lose access to the internet. I've added these lines to the file:
```

auto wlan0
iface wlan0 inet static
    address 192.168.1.200
    netmask 255.255.255.0
    gateway 192.168.1.1

```

This changes the output of ifconfig, but I can no longer connect to the WiFi.

---

### Post by chili555 on 2017-03-14
> auto wlan0
iface wlan0 inet static
    address 192.168.1.200
    netmask 255.255.255.0
    gateway 192.168.1.1Ouch!

Please see: [http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552)

You need but lack the SSID, password and DNS.

---

### Post by awesomedude on 2017-03-14
Thanks, that got the static IP to work with an internet connection. I still cannot connect to the Raspberry Pi via ssh. 
```

$ ssh username@192.168.1.200
ssh: connect to host 192.168.1.200 port 22: Connection refused

```

---

### Post by chili555 on 2017-03-14
Is ssh running?```
service ssh status
```Is it listening on port 22?```
sudo netstat -anp | grep -i ssh
```I'm on thin ice here; I flunked ssh back in my old Torvalds High School days.  :-(

---

### Post by awesomedude on 2017-03-14
Turns out it was disabled. So I just restarted it.
```
service ssh restart
```
Thanks for your assistance.

---

### Post by chili555 on 2017-03-14
Awesome! Glad it's working.

Please use thread tools at the top of the forum to mark Solved. The searchers will appreciate it.

---

