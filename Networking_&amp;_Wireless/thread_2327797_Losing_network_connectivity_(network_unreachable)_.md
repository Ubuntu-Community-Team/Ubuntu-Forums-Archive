---
title: "Losing network connectivity (network unreachable) after a period of time"
date: 2016-06-14
forum: Networking &amp; Wireless
---

### Post by Jefferson_Hudson on 2016-06-14
I am running Ubuntu server 14.04, but I was having this issue on 16.04 as well. Switch back to 14.04 to see if that would fix it.

The machine is running inside a KVM instance. 

The problem is that I keep losing the connection to my default gateway. I'm not *really* losing it though, because if I watch the local traffic I can see my requests being sent and responses being returned. For some reason the machine doesn't see this. 

I can still talk to other machines on the LAN without a problem. It's just the gateway and anything upstream of the gateway that goes bye-bye.

If I bounce the interface connectivity comes right back up. 

The interface is configured like so:
```
auto eth0
iface eth0 inet static
  address 10.200.17.66
  netmask 255.255.255.0
  gateway 10.200.17.1
  dns-nameservers 10.200.17.253
  dns-search <domain>.com
```

dhclient isn't running, and in fact cannot run because I disabled it.
```
root@mv-relay:~# ps aux | grep dhclient
root      3675  0.0  0.0  11740   920 pts/0    S+   15:52   0:00 grep --color=auto dhclient
root@mv-relay:~# ls -la /sbin/dhclient
-rw-r--r-- 1 root root 1668160 Jan 11 13:20 /sbin/dhclient
root@mv-relay:~# ls -la /sbin/dhclient-script
-rw-r--r-- 1 root root 14484 Jan 11 13:20 /sbin/dhclient-script
```

I see these references to dhclient/networkmanager/etc in the syslog during bootup, but (except for the first) those file locations don't exist on the machine
```
Jun 14 15:53:48 mv-relay kernel: [    1.512503] type=1400 audit(1465919628.206:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=414 comm="apparmor_parser"
Jun 14 15:53:48 mv-relay kernel: [    1.512518] type=1400 audit(1465919628.206:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=414 comm="apparmor_parser"
Jun 14 15:53:48 mv-relay kernel: [    1.512525] type=1400 audit(1465919628.206:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=414 comm="apparmor_parser"
Jun 14 15:53:48 mv-relay kernel: [    1.513295] type=1400 audit(1465919628.206:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=414 comm="apparmor_parser"
Jun 14 15:53:48 mv-relay kernel: [    1.513305] type=1400 audit(1465919628.206:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=414 comm="apparmor_parser"
Jun 14 15:53:48 mv-relay kernel: [    1.513675] type=1400 audit(1465919628.206:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=414 comm="apparmor_parser"

```



I'm not sure how to proceed in troubleshooting. Please advise.

---

### Post by Jefferson_Hudson on 2016-06-14
I've discovered that there appear to be two devices with the same MAC address on the local network. I can't figure out why that is though.
```
root@dns:~# arp -n
10.200.17.66             ether   52:54:00:63:a1:c4   C                     eth0
10.200.17.203            ether   52:54:00:63:a1:c4   C                     eth0
```

When I restart the interface on machine *.66, this is what the arp table changes to:
```
root@dns:~# arp -n
10.200.17.66             ether   52:54:00:63:a1:c4   C                     eth0
10.200.17.203                    (incomplete)                              eth0
```

Why does .66 seem to be misreporting itself as *.203?

---

### Post by Jefferson_Hudson on 2016-06-14
Using arp-scan I was able to determine that there was another machine attempting to use this IP address. Problem solved!

---

