---
title: "Pro/Wireless 3945ABG issues [recommended course of action]"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by aqualad on 2007-03-26
Okay, so I think some higher power has taken control and sacrificed my laptop's wireless for my brother's desktop wireless (it seems the moment I fix one the other one breaks)

So here's the deal, my 6.10 laptop suddenly lost wireless connectivity.  The only changes I made were:

-Changed router Authentication type to Shared
-Removed Wireless MAC Filter and Access rules on router

I made no changes to my laptop, so I don't understand where this problem is coming from.  The eth0 still works, but when I try
```
sudo ifup eth1
```
I get
```
aqualad@lappy:~$ sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:02:45:4c:e9
Sending on   LPF/eth1/00:13:02:45:4c:e9
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Other information about the problem:

```
aqualad@lappy:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:16:B6:43:0E:B9
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=94/100  Signal level=-35 dBm  Noise level=-35 dBm
                    Extra: Last beacon: 20ms ago

sit0      Interface doesn't support scanning.
```

```
aqualad@lappy:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"linksys"  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

sit0      no wireless extensions.

```

```
aqualad@lappy:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp






iface eth1 inet dhcp
wireless-essid linksys

auto eth1

auto eth0

```


I hope this is enough.  I figure I should either try to reinstall ipw3945 from source or try to figure out what setting needs changed. As far as I can tell **it won't even connect to the router when it's unencrypted with no security**

Thanks for the help :] gotta love the community!

---

### Post by ubuntnewb on 2007-03-26
Hmm. I can't even get that far =(
[http://ubuntuforums.org/showthread.php?t=393911](http://ubuntuforums.org/showthread.php?t=393911)

---

### Post by Floppyjoe on 2007-03-26
Aqualad, By shared authentication do you mean WPA-PSK? If so you need to set up WPA on your computer.

This link will show you the way if that is the case:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

### Post by chili555 on 2007-03-26
> Changed router Authentication type to SharedIn Linksys routers, this means you both *must* use the same key. I see no key configured in interfaces. 
Please change the router back to Open protocol and try again.

---

### Post by aqualad on 2007-03-26
Hah, wow, thanks.  I guess in my mangling I didn't pay attention to the fact that Shared is not what I need for WEP.  Changed it back and problem solved.  Thanks. Now let's just pray my brother's computer stayed online ;]

---

