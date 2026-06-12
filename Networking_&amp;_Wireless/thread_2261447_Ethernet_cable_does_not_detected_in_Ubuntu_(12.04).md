---
title: "Ethernet cable does not detected in Ubuntu (12.04)"
date: 2015-01-19
forum: Networking &amp; Wireless
---

### Post by aryan4 on 2015-01-19
Hello, I have Dell Vostro 270s system with fresh ubuntu installation. When I start the system, It detects ethernet cable, but soon after system loose it. 
here is my **ifconfig** result

> eth0      Link encap:Ethernet  HWaddr a4:1f:72:84:2e:80  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4271 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:418032 (418.0 KB)  TX bytes:418032 (418.0 KB)

wlan0     Link encap:Ethernet  HWaddr bc:85:56:d1:ab:a9  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::be85:56ff:fed1:aba9/64 Scope:Link
          inet6 addr: fd58:3b59:645b:0:2554:e8f8:c47b:e885/64 Scope:Global
          inet6 addr: fd58:3b59:645b:0:be85:56ff:fed1:aba9/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:150683 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
  RX bytes:172379210 (172.3 MB)  TX bytes:9617472 (9.6 MB)


And this is** /etc/network/interfaces** file.


> auto lo
iface lo inet loopback


I have tried every solution given online on this forum, askubuntu and thomashardware. but it doesn't help. Can anyone help me fixing this?

---

### Post by chait3 on 2015-01-19
Hi,
  Firstly, what do you mean by 'ethernet cable not detected' ? 
Assuming you are not able to set an ip address, you can set it in /etc/network/interfaces file by appending the following lines:

> auto <your interface name>
iface <your interface name> inet <static / dhcp>

If you are using dhcp, above lines would suffice, else you need to append these one:

> address <your ip address>
netmask <your netmask>
gateway <your gateway>

After this, you need to restart network service:

> sudo /etc/init.d/networking restart

---

### Post by Hadaka on 2015-01-19
hi please copy and paste..
```
lspci -n | egrep '0200|0280' | awk '{print$2}'
lsmod | egrep 'wl|b43'
rfkill list all | grep -i yes
```
post the output
thanks.

---

