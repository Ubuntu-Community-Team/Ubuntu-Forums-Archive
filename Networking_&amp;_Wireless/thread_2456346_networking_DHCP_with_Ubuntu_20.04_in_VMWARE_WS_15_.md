---
title: "networking DHCP with Ubuntu 20.04 in VMWARE WS 15 - fail"
date: 2021-01-09
forum: Networking &amp; Wireless
---

### Post by petersk on 2021-01-09
I am running opnsense as my dhcp server. I did a minor mod disabling ipv6 on my lan and now my Ubuntu won't connect properly. See below: 

```
# systemctl status network-manager
&#9679; NetworkManager.service - Network Manager
     Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2021-01-09 17:31:22 MST; 5min ago
       Docs: man:NetworkManager(8)
   Main PID: 3545 (NetworkManager)
      Tasks: 3 (limit: 9453)
     Memory: 6.8M
     CGroup: /system.slice/NetworkManager.service
             &#9492;&#9472;3545 /usr/sbin/NetworkManager --no-daemon

Jan 09 17:37:06 ubuntu NetworkManager[3545]: <info>  [1610239026.4399] device (ens33): state change: unavailable -> disconnected (reason 'carrier-changed', sys-ifac>
Jan 09 17:37:06 ubuntu NetworkManager[3545]: <info>  [1610239026.4408] policy: auto-activating connection 'Wired connection 1' (eb75c5a5-c7fa-3513-81bf-6fc8e3fbb483)
Jan 09 17:37:06 ubuntu NetworkManager[3545]: <info>  [1610239026.4413] device (ens33): Activation: starting connection 'Wired connection 1' (eb75c5a5-c7fa-3513-81bf>
Jan 09 17:37:06 ubuntu NetworkManager[3545]: <info>  [1610239026.4415] device (ens33): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'manag>
Jan 09 17:37:06 ubuntu NetworkManager[3545]: <info>  [1610239026.4418] manager: NetworkManager state is now CONNECTING
Jan 09 17:37:06 ubuntu NetworkManager[3545]: <info>  [1610239026.4420] device (ens33): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jan 09 17:37:06 ubuntu NetworkManager[3545]: <info>  [1610239026.4447] device (ens33): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Jan 09 17:37:06 ubuntu NetworkManager[3545]: <info>  [1610239026.4449] dhcp4 (ens33): activation: beginning transaction (timeout in 45 seconds)
Jan 09 17:37:06 ubuntu NetworkManager[3545]: libndp: ndp_sock_open: Failed to create ICMP6 socket.
Jan 09 17:37:06 ubuntu NetworkManager[3545]: <error> [1610239026.4482] device (ens33): addrconf6: failed to start neighbor discovery: failure creating libndp socket>
```


I then disable IPv6 in the network manager GUI:
```
systemctl status network-manager
&#9679; NetworkManager.service - Network Manager
     Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2021-01-09 17:47:09 MST; 2s ago
       Docs: man:NetworkManager(8)
   Main PID: 4745 (NetworkManager)
      Tasks: 4 (limit: 9453)
     Memory: 4.4M
     CGroup: /system.slice/NetworkManager.service
             &#9492;&#9472;4745 /usr/sbin/NetworkManager --no-daemon

Jan 09 17:47:09 ubuntu NetworkManager[4745]: <info>  [1610239629.3162] device (docker0): state change: unavailable -> disconnected (reason 'none', sys-iface-state: >
Jan 09 17:47:09 ubuntu NetworkManager[4745]: <info>  [1610239629.3171] device (ens33): state change: unavailable -> disconnected (reason 'none', sys-iface-state: 'm>
Jan 09 17:47:09 ubuntu NetworkManager[4745]: <info>  [1610239629.3177] policy: auto-activating connection 'Wired connection 1' (eb75c5a5-c7fa-3513-81bf-6fc8e3fbb483)
Jan 09 17:47:09 ubuntu NetworkManager[4745]: <info>  [1610239629.3180] device (ens33): Activation: starting connection 'Wired connection 1' (eb75c5a5-c7fa-3513-81bf>
Jan 09 17:47:09 ubuntu NetworkManager[4745]: <info>  [1610239629.3181] device (ens33): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'manag>
Jan 09 17:47:09 ubuntu NetworkManager[4745]: <info>  [1610239629.3183] manager: NetworkManager state is now CONNECTING
Jan 09 17:47:09 ubuntu NetworkManager[4745]: <info>  [1610239629.3189] device (ens33): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jan 09 17:47:09 ubuntu NetworkManager[4745]: <info>  [1610239629.3213] agent-manager: agent[fc8379889bbb8af1,:1.74/org.gnome.Shell.NetworkAgent/1000]: agent registe>
Jan 09 17:47:09 ubuntu NetworkManager[4745]: <info>  [1610239629.3215] device (ens33): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Jan 09 17:47:09 ubuntu NetworkManager[4745]: <info>  [1610239629.3217] dhcp4 (ens33): activation: beginning transaction (timeout in 45 seconds)
root@ubuntu:/home/kurt# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: ens33: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:0c:29:f3:0c:45 brd ff:ff:ff:ff:ff:ff
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:38:f3:6a:72 brd ff:ff:ff:ff:ff:ff
```

As you can see, I don't get an ip address assigned by DHCP.
I've tried adding a static IP and I get various failures.  The one that pops up is "connection failed" activation of network connection failed"

I don't understand how every other device on my network is fine with the OPNSense change but ubuntu has terrible issues.
Kurt

---

### Post by TheFu on 2021-01-12
I don't have any clue, but kernel parameters are needed at boot to disable ipv6. Is the grub.conf modified for that purpose?
I stopped using network-manager about a decade ago after some nasty issues, but my network isn't very standard.
BTW, I use opnsense too. 
I do not use anything from VMware nor any docker stuff.

---

