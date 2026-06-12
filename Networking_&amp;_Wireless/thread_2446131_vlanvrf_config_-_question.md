---
title: "vlan/vrf config - question"
date: 2020-06-25
forum: Networking &amp; Wireless
---

### Post by ahiyaz on 2020-06-25
hi

im trying configuring vlan interface that assign to vrf on a 20.04 ubuntu desktop machine.
ive used iproute2 for that.
```

```
ip link add link ens160 name ens160.105 type vlan id 105
ip link add 105 type vrf table 5
ip link set dev 105 up
ip rule add iif 105 table 5
ip rule add oif 105 table 5
ip link set ens160.105 master 105
ip link set ens160.105   up
ip addr add 10.1.5.3/24  dev  ens160.105
ip route add 0.0.0.0/0 via 10.1.5.1 table 5
```
[CODE]
```[/CODE]

at this point the vlan int works and i can ping through the vrf.
but when im resetting the machine all config [FONT=Assistant][COLOR=#333333]disappear.[/COLOR][/FONT]
[FONT=Assistant][COLOR=#333333]another issue is that i cant configure dhcp and i cant configure dns (name servers) for that vrf.[/COLOR][/FONT]

[FONT=Assistant][COLOR=#333333]ive tried using netplan but it didn't work.[/COLOR][/FONT]

[FONT=Assistant][COLOR=#333333]any ideas?
ill appreciate any help

thanks all[/COLOR][/FONT]

---

