---
title: "ubuntu 12.04 vpn connection not established"
date: 2016-07-02
forum: Networking &amp; Wireless
---

### Post by iebo on 2016-07-02
hello

i was using ubuntu 12.04 for 2 years and i loved it i know it will be dropped soon, a  month ago i did upgrade to ubuntu 14 but rolled back because its take  much memory 

now i have fresh  pangolin install ,i installed most of my fav programs but vpn not working !

please help me setup vpn connection , i searched a lot but there no single solution for my problem.

tail -f /var/log/syslog

```
 Jul  2 10:04:13 HP-620 NetworkManager[10046]: <warn> VPN plugin failed: 1
Jul  2 10:04:13 HP-620 NetworkManager[10046]: <info> VPN plugin state changed: stopped (6)
Jul  2 10:04:13 HP-620 NetworkManager[10046]: <info> VPN plugin state change reason: 0
Jul   2 10:04:13 HP-620 NetworkManager[10046]: <warn> error  disconnecting VPN: Could not process the request because no VPN  connection was active.
Jul  2 10:04:13 HP-620 NetworkManager[10046]:  <info> Policy set 'Wired connection' (eth0) as default for IPv4  routing and DNS.
Jul  2 10:04:18 HP-620 NetworkManager[10046]: <info> VPN service 'pptp' disappeared


```

```
 sudo nmcli con up id reactorvpn
[sudo] password for HP-620: 
Active connection state: unknown
Active connection path: /org/freedesktop/NetworkManager/ActiveConnection/6
state: VPN connecting (need authentication) (2)
state: VPN connecting (3)
state: VPN connecting (getting IP configuration) (4)
Error: Connection activation failed: unknown reason.


```


things i tried already 

-adding 
[vpn-secrets]

password-flags=0

to /etc/NetworkManager/system-connections

- changing permissions  on

/etc/NetworkManager/VPN
&
/etc/NetworkManager/system-connections


- removing and reinstall 
ppp package/ network-manager etc

 
-this [http://wiki.ubuntu.com/VPN](http://wiki.ubuntu.com/VPN)

---

### Post by iebo on 2016-07-02
no idea ??

vpn connection failed

---

