---
title: "[ VPN ] vpn connection makes Internet slow"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by dmitrievich on 2008-04-15
I have remote Windows VPN server I want to connect to
I use kubuntu 7.10 and knetworkmanager
Everything works OK, except speed of connection
After enabling VPN internet connection (and vpn connection) become very slow

Somewhere on ubuntuforums I got info that netstat -rn should tell me something useful, I'm sure it does, but I don't understand this info :)

My normal routes are
```
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG        0 0          0 eth0
```

After enabling VPN
```
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
vpn.ser.ver.ip    192.168.1.254   255.255.255.255 UGH       0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 ppp0
```

Which route should I remove / edit / add?

Thanks in advance

---

### Post by SpaceTeddy on 2008-04-15
what exactly is slow ? the routeing entries look fine if you connect to a windows VPN (ppp0 is the device which is used for the connection). Was the VPN faster in the past ? what did you use to connect then ? i'd need more info if i was to find a reason for why it is slow...

my first guess is that the vpn-server has limited upload capacity and having to share that among lots of hosts. Since windows vpn always routes every and anything over the vpn connecetion, this can be a cause to slow down things A LOT.

Another reason could be that your dns servers are not updates, and suddenly some dns entries time out, giving you a two to four second wait time before a nameserver is found that can be reached and resolve names... 

but these are all guesses. without more info, it is impossible to say what is happening...

---

