---
title: "ufw Not Allowing Hostname Resolution"
date: 2017-07-12
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2017-07-12
I have a VPN running. To act as a "killswitch" I have the following rules in place under ufw:

```

   # allow local network traffic
ufw allow out from 192.168.1.0/24 to any
ufw allow in from 192.168.1.0/24 to any

   # allow traffic via the tun0 connection
ufw allow in on tun0 from any to any
ufw allow out on tun0 from any to any

   # allow VPN to connect through the firewall
ufw allow out 1194/udp   # 1197 for OpenVPN
ufw allow in 1194/udp    # 1197 for OpenVPN

   # deny all other traffic
sudo ufw default deny incoming
sudo ufw default deny outgoing

```

Everything seems to work fine with one exception. When I go to octopi.local, the system is unable to resolve that hostmane to an IP address. I can got the IP address manually, but since it is dynamic, that is not a very good option. I can disable the firewall, and then connect to octopi.local.What do I need to do to allow the resolution service to work through the firewall?

---

### Post by rebeltaz on 2017-07-12
As always, I may have answered my own question, but I need verification that the rules I have are "safe" for what I want them to do - block all traffic not going through the VPN with the exception of local network traffic.

I changed the rules for local traffic to this:
```

sudo ufw allow out from 192.168.1.0/24 to any
sudo ufw allow in from 192.168.1.0/24 to any
sudo ufw allow out from any to 192.168.1.0/24
sudo ufw allow in from any to 192.168.1.0/24

```


Thoughts and/or criticism?

---

### Post by rebeltaz on 2017-07-14
I've also noticed that the firewall doesn't seem to be working correctly. With the following rules:

```

Default: deny (incoming), deny (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
Anywhere on tun0           ALLOW IN    Anywhere                  
1194/udp                   ALLOW IN    Anywhere                  
Anywhere                   ALLOW IN    192.168.1.0/24            
192.168.1.0/24             ALLOW IN    Anywhere                  
Anywhere (v6) on tun0      ALLOW IN    Anywhere (v6)             
1194/udp (v6)              ALLOW IN    Anywhere (v6)             

Anywhere                   ALLOW OUT   Anywhere on tun0          
1194/udp                   ALLOW OUT   Anywhere                  
192.168.1.0/24             ALLOW OUT   Anywhere                  
Anywhere                   ALLOW OUT   192.168.1.0/24            
Anywhere (v6)              ALLOW OUT   Anywhere (v6) on tun0     
1194/udp (v6)              ALLOW OUT   Anywhere (v6)       

```

when I disable the VPN, and I am just connected directly to the network, I am still able to surf the net and my actual IP is reported back when queried.

---

