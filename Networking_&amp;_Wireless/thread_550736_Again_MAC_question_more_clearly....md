---
title: "Again MAC question more clearly..."
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by cd-r80 on 2007-09-14
When spoofing Mac I cannot get new IP. Is the problem Dapper/networking/DHCP Client or broken bridge Router or ISP have made something? I have a right to 5 IPs!!! Here you can see very clearly what happens. I have 3 choices: Change Linux distro, change ISP or hit the router to the wall. 
Changing MAC was possible earlier when I used Hoary. Well this is the last time I try to ask this more clearly now, more is spam. Any clue?

root# /etc/init.d/networking stop
 * Deconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3

Listening on LPF/eth0/aa:aa:aa:aa:aa:aa
Sending on   LPF/eth0/aa:aa:aa:aa:aa:aa
Sending on   Socket/fallback
DHCPRELEASE on eth0 to x.x.x.x. port 67
                                                                                           [ ok ]
root# macchanger -e eth0
Current MAC: aa:aa:aa:aa:aa:aa (Pro-nets Technology Corporation)
Faked MAC:   bb:bb:bb:bb:bb:bb (Pro-nets Technology Corporation)

root# /etc/init.d/networking restart
 * Configuring network interfaces... Internet Systems Consortium DHCP Client V3.0.3

Listening on LPF/eth0/bb:bb:bb:bb:bb:bb
Sending on   LPF/eth0/bb:bb:bb:bb:bb:bb
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

root# ifconfig
eth0      Link encap:Ethernet  HWaddr bb:bb:bb:bb:bb:bb
          No IP

root# ifconfig eth0 down

MAC BACK TO ORIGINAL!
root# macchanger -m aa:aa:aa:aa:aa:aa eth0
Current MAC: bb:bb:bb:bb:bb:bb (Pro-nets Technology Corporation)
Faked MAC:   aa:aa:aa:aa:aa:aa (Pro-nets Technology Corporation)

root# /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3

Listening on LPF/eth0/aa:aa:aa:aa:aa:aa
Sending on   LPF/eth0/aa:aa:aa:aa:aa:aa
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from x.x.x.x.
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from x.x.x.x.
bound to b.b.b.b -- renewal in 14115 seconds.
                                                                                            [ ok ]
eth0      Link encap:Ethernet  HWaddr aa:aa:aa:aa:aa:aa
          inet addr:b.b.b.b  Bcast:b.b.b.255  Mask:255.255.240.0
IP ok!

---

