---
title: "Having VPN as Default Connection"
date: 2021-03-18
forum: Networking &amp; Wireless
---

### Post by Quarkrad on 2021-03-18
I have successfully installed a vpn using Openvpn using Surfshark as the provider.  Using Network Manager (Ubuntu Mate 20.04) I can switch from my wired ethernet connect to the vpn via the network manager gui using *vpn connections*.  When using non vpn I get:

```
dad@dadubuntu:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether d0:bf:9c:88:4b:bc brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.64/24 brd 192.168.1.255 scope global dynamic noprefixroute eno1
       valid_lft 85681sec preferred_lft 85681sec
    inet6 2a00:23c8:4182:ba00:4d6:ad1:6dc0:a62c/64 scope global temporary dynamic 
       valid_lft 604080sec preferred_lft 85269sec
    inet6 2a00:23c8:4182:ba00:d75e:e5a4:a2fd:e6a3/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 315359974sec preferred_lft 315359974sec
    inet6 fdaa:bbcc:ddee:0:4d6:ad1:6dc0:a62c/64 scope global temporary dynamic 
       valid_lft 604080sec preferred_lft 85269sec
    inet6 fdaa:bbcc:ddee:0:9025:666f:cfee:d3e1/64 scope global mngtmpaddr noprefixroute 
       valid_lft forever preferred_lft forever
    inet6 fe80::d409:6596:19df:c720/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:98:bb:e2 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
4: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc fq_codel master virbr0 state DOWN group default qlen 1000
    link/ether 52:54:00:98:bb:e2 brd ff:ff:ff:ff:ff:ff
dad@dadubuntu:~$ 

```

And when using vpn I get:

```
dad@dadubuntu:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether d0:bf:9c:88:4b:bc brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.64/24 brd 192.168.1.255 scope global dynamic noprefixroute eno1
       valid_lft 85610sec preferred_lft 85610sec
    inet6 2a00:23c8:4182:ba00:4d6:ad1:6dc0:a62c/64 scope global temporary dynamic 
       valid_lft 604008sec preferred_lft 85197sec
    inet6 2a00:23c8:4182:ba00:d75e:e5a4:a2fd:e6a3/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 315360000sec preferred_lft 315360000sec
    inet6 fdaa:bbcc:ddee:0:4d6:ad1:6dc0:a62c/64 scope global temporary dynamic 
       valid_lft 604008sec preferred_lft 85197sec
    inet6 fdaa:bbcc:ddee:0:9025:666f:cfee:d3e1/64 scope global mngtmpaddr noprefixroute 
       valid_lft forever preferred_lft forever
    inet6 fe80::d409:6596:19df:c720/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:98:bb:e2 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
4: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc fq_codel master virbr0 state DOWN group default qlen 1000
    link/ether 52:54:00:98:bb:e2 brd ff:ff:ff:ff:ff:ff
6: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 100
    link/none 
    inet 10.8.8.5/24 brd 10.8.8.255 scope global noprefixroute tun0
       valid_lft forever preferred_lft forever
    inet6 fe80::489d:a6dd:c0a1:1543/64 scope link stable-privacy 
       valid_lft forever preferred_lft forever
dad@dadubuntu:~$ 

```

So .... when I switch/enable the vpn I get the tun0: interface.  What I would like to do, if possible, but not been able to find out how to do it so far, is whether it is possible to make my vpn connection the Default Connection when I boot, rather than have to switch to it manually.

Netplan config is:

```
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
```

---

### Post by TheFu on 2021-03-18
There cannot be a VPN until after the local LAN and WAN are up.  Priorities for networking are control in the 'metric' value.  Normally, you'd see this by looking at the routing table. The lowest number gets priority for the subnet served.  Generally, we don't want our LAN connections to use the VPN - that wouldn't work. You'd not be able to print to a LAN printer or access samba/NFS shared storage or stream videos from/to your video player-stick.

Anyway .... 
```
ip route | column -t
```
Should show the needed information.  Well, crap. It doesn't.  We have to go old-school.

```
route -n
``` definitely shows the metric column. Post that if you need more help.

BTW, I don't use network-manager, so anything outside general networking related to that will need someone else to answer.

---

### Post by thumper76 on 2021-03-19
You can set up your VPN to start automatically from the  "Startup Applications" program. There's a Gui apt you can use. When I installed Riseup VPN it set this up for me at installation.

---

### Post by tigi on 2022-03-04
> **thumper76 said:**
> You can set up your VPN to start automatically from the  "Startup Applications" program. There's a Gui apt you can use. When I installed Riseup VPN it set this up for me at installation.

Thanks for your advise, it helped me in part.
In the "Startup Applications" program, i have added the command:  /snap/bin/riseup-vpn.launcher  .
Now when i start my computer, the riseup-vpn program starts in "disable" mode, and shows a little icon.
Then i can enable it manually from the icon or from the riseup-vpn GUI.
I did a speed test and found that my internet connection is the same when riseup-vpn is not launched or launched in disabled mode;
then if i enable it, the speed gets ~ 10x lower.
So it may be ok that i need to enable it manually.

---

