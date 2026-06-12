---
title: "Two interfaces on one interface"
date: 2020-03-31
forum: Networking &amp; Wireless
---

### Post by sniper8752 on 2020-03-31
I noticed this on my Ubuntu 18 desktop:
```
inet 192.168.2.2/24 brd 192.168.2.255 scope global dynamic noprefixroute eth0       valid_lft 391sec preferred_lft 391sec
    inet 192.168.2.4/24 brd 192.168.2.255 scope global secondary noprefixroute eth0
       valid_lft forever preferred_lft forever

```
Why do I have two interfaces, and what is the difference?

---

### Post by sniper8752 on 2020-04-03
*bump*

---

### Post by dmnur on 2020-04-03
Looks like you have two IP addresses on one interface — one (192.168.2.2) from DHCP and the other (192.168.2.4) is static.

Not sure why. Check your network configuration.

In case you don't find anything, show us your network configuration. It is probably managed by NetworkManager, so use this command:
```
nmcli c show
```

It will show a list of connection profiles, like this:
```
NAME                UUID                                  TYPE      DEVICE
Wired connection 1  b9afbb18-75ca-11ea-894f-67a5dd7a5691  ethernet  --
```

Then run **nmcli c show *PROFILE_NAME*** and show us the output. In the above example the profile is named **Wired connection 1**, so the command would be:
```
nmcli c show 'Wired connection 1'
```

---

### Post by sniper8752 on 2020-04-06
I noticed they are both now dynamic.  I stopped the isc-dhcp-server on my server, and I had no ips.  I started it up again, and go the 2 ips again.  
Looking in the dhcpd.leases file on the server, I see that these two IPs are listed, and have just about the same start time (within a few microseconds).  I believe there are two wireless connection utilities working, but I am not sure.  I know of /etc/network/interfaces, but don't have anything in there defined for this interface.  I've defined this interface in netplan which I am not too familiar with, and set it to dhcp.  
Also, I've noticed that I can reach my dhcp server, but can't reach other internal IPs.

---

