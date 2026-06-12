---
title: "Wireless OK but Wired stopped after a few days"
date: 2021-12-03
forum: Networking &amp; Wireless
---

### Post by themulk on 2021-12-03
Dear reader,

I have a peculiar problem with my network. After I recently installed Ubuntu 21.10 on my Dell Laptop, everything worked fine. For a project I had to install dnsmasq parallel to systemd-resolved and docker, still after that everything was fine, even after reboot. One day the wired connection I was using just stopped working while the computer was running and did not return. Wireless however is still working fine. In settings, the whole "network-setting" for wired is no longer existing.
It is a dual install with Ubuntu 18.04. If I switch back to that, wired is running fine, also with docker and dnsmasq but I think I shut down systemd-resolved for that.

Does anyone has an idea, what might cause this problem?
I figured, that I "just" tempered with dns and that wireless is still working, it is not a problem with the network as such. Also the latest drivers have been installed this week per autoupdate.

This is from ```
ip address show
```, I tried to filter the docker network

```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever

2: enp0s31f6: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether c8:f7:50:43:fd:c2 brd ff:ff:ff:ff:ff:ff

3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether d4:3b:04:55:5e:b5 brd ff:ff:ff:ff:ff:ff
    inet 192.168.28.197/24 brd 192.168.28.255 scope global dynamic noprefixroute wlp2s0
       valid_lft 603536sec preferred_lft 603536sec
    inet6 fe80::e45f:6d13:ac17:a37b/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

411: enxc8f750c0ff27: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether c8:f7:50:c0:ff:27 brd ff:ff:ff:ff:ff:ff

```


```
nmcli d
``` shows me no wired connection
```

wlp2s0           wifi      connected  Lair       
docker0          bridge    unmanaged  --         
docker_gwbridge  bridge    unmanaged  --         
enp0s31f6        ethernet  unmanaged  --         
enxc8f750c0ff27  ethernet  unmanaged  --
[...]
lo               loopback  unmanaged  --         
p2p-dev-wlp2s0   wifi-p2p  unmanaged  -- 

```

---

