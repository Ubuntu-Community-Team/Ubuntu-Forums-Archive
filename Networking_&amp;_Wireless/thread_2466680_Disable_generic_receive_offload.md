---
title: "Disable generic receive offload"
date: 2021-09-02
forum: Networking &amp; Wireless
---

### Post by dain-bramage on 2021-09-02
I am running Ubuntu 20.04

I have a separate NIC I use for Wireshark captures. The NIC is performing generic receive offload. This means I am not actually capturing the packets as they appear on the wire.

I can manually turn this off with 

```
[COLOR=#000000][COLOR=#000000][FONT=Menlo]ethtool [/FONT][/COLOR][/COLOR][COLOR=#666600][FONT=Menlo]-[/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Menlo]K enp4s0 gro off[/FONT][/COLOR][/COLOR]
```

but this wont survive a reboot.

Can anyone tell me the correct syntax for an entry into [COLOR=#000000][FONT=Monaco]/etc/netplan/01-network-manager-[/FONT][/COLOR][COLOR=#2060A0][FONT=Monaco]all[/FONT][/COLOR][COLOR=#000000][FONT=Monaco].yaml [FONT=arial]that would disable GRO automatically for this NIC on boot?[/FONT][/FONT][/COLOR]

---

### Post by TheFu on 2021-09-02
I've never seen a post-up command in netplan like we had with the interfaces file.  If you can't find that capability in the netplan documentation (netplan.io), then the best way I know would be to create a new systemd unit file to do it that has a strong dependency on networking being up.  There are a number of different network unit files, so you'll need to look up which is actually the one that brings up interfaces.

BTW, you'll need to put the full path to ethtool into the command. Don't expect there to be any PATH set that early in boot.

---

