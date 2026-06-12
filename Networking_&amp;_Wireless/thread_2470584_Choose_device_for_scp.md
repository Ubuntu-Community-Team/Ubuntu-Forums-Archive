---
title: "Choose device for scp"
date: 2022-01-05
forum: Networking &amp; Wireless
---

### Post by quentchen81 on 2022-01-05
Hi,
 i have enp1s0 (lan) and wlp2s0 (wlan) on my „server“. Most of the traffic goes through enp1s0. That is fine. But I try to use wlp2s0 for special things:
 ssh -B wlp2s0 XXX.XXX.XXX.XXX
 but this does not work.
 
 
 ip route show
 default via 192.168.0.1 dev enp1s0 proto dhcp src 192.168.0.84 metric 100  
 default via 192.168.179.1 dev wlp2s0 proto dhcp metric 600  
 192.168.0.0/24 dev enp1s0 proto kernel scope link src 192.168.0.84  
 192.168.0.1 dev enp1s0 proto dhcp scope link src 192.168.0.84 metric 100  
 192.168.179.0/24 dev wlp2s0 proto kernel scope link src 192.168.179.56 metric 600  
 
 
 ssh -B enp1s0 XXX.XXX.XXX.XXX works fine. But it is the same as ssh XXX.XXX.XXX.XXX
 
 
 when I unplug the lan-cable ssh -B wlp2s0 XXX.XXX.XXX.XXX works. But it is the same as ssh XXX.XXX.XXX.XXX
 
 
 my computer seams to try to use the gateway 192.168.0.1 when using the ip 192.168.179.56. And this can not work.
 
 
 Is there a workaround?
 
 
 (I try to use scp to copy much data through wlan and I configured my Lan that this hase low priority so this will not yam my internet connection.)

  
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:    20.04
Codename:    focal

---

### Post by quentchen81 on 2022-01-05
Hi,
 now it works. Here my solution:
 
 
 sudo ip route add table 1921680    default via 192.168.0.1 dev enp1s0
 sudo ip route add table 192168179    default via 192.168.179.1 dev wlp2s0
 sudo ip rule add from 192.168.0.0/22   lookup 1921680
 sudo ip rule add from 192.168.179.0/24   lookup 192168179
 
 
 now
 scp -oBindInterface=wlp2s0 /home/yy/zz/* XXX.XXX.XXX.XXX:/home/yy/
 pushes data through wlan :-D

---

### Post by mIk3_08 on 2022-01-05
> **quentchen81 said:**
> Hi,
 now it works. Here my solution:
 
 
 sudo ip route add table 1921680    default via 192.168.0.1 dev enp1s0
 sudo ip route add table 192168179    default via 192.168.179.1 dev wlp2s0
 sudo ip rule add from 192.168.0.0/22   lookup 1921680
 sudo ip rule add from 192.168.179.0/24   lookup 192168179
 
 
 now
 scp -oBindInterface=wlp2s0 /home/yy/zz/* XXX.XXX.XXX.XXX:/home/yy/
 pushes data through wlan :-D
Thanks for sharing. This might help others who's experiencing same problem with yours. Cheers 
God Bless.

---

### Post by TheFu on 2022-01-05
I don't think adding the device to the ssh command options matters. It is a routing issue.  Set the routing to use the device with a lower (i.e. higher) priority than the other device and all traffic should go that way, using the device with the lowest "metric".

---

