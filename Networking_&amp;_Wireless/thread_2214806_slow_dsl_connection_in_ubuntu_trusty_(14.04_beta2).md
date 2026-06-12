---
title: "slow dsl connection in ubuntu trusty (14.04 beta2)?"
date: 2014-04-03
forum: Networking &amp; Wireless
---

### Post by shamsat on 2014-04-03
I am running ubuntu 13.10 (saucy), dsl connection is normal with it's default speed no problem, i also installed the ubuntu 14.04 beta2 (trusty), suprisingly the dsl connection is running very slow in this version of ubuntu, i use the same pc an dsl router for both ubuntu 13.10 and 14.04 beta2, i use wired connection at the time.
Any idea please?

---

### Post by chili555 on 2014-04-03
Let's take a look at some diagnostics. Please open a terminal and run and post from 14.04:```
nm-tool
ping -c3 www.google.com
ping -c3 8.8.8.8
```Thanks.

---

### Post by shamsat on 2014-04-04
Thanks for reply, these are the output of commands:
> 
# nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        5C:07:71:58:62:3D

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [ROUTE NET ] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        B8:76:3F:C0:28:89

  Capabilities:
    Speed:           5 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *ROUTE NET :      Infra, C6:D5:A3:E5:26:93, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



> 
# ping -c3 [www.google.com](www.google.com)
PING [www.google.com](www.google.com) (110.93.194.19) 56(84) bytes of data.
64 bytes from [www.google.com](www.google.com) (110.93.194.19): icmp_seq=1 ttl=58 time=40.4 ms
64 bytes from [www.google.com](www.google.com) (110.93.194.19): icmp_seq=2 ttl=58 time=42.3 ms
64 bytes from [www.google.com](www.google.com) (110.93.194.19): icmp_seq=3 ttl=58 time=41.0 ms

--- [www.google.com](www.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 40.492/41.271/42.317/0.768 ms


> 
# ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=44 time=170 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=44 time=170 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=44 time=177 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 170.052/172.921/177.770/3.480 ms


---

### Post by chili555 on 2014-04-04
>  i use the same pc an dsl router for both ubuntu 13.10 and 14.04 beta2, i use wired connection at the time.But we see here:> NetworkManager Tool

State: connected (global)

[COLOR="#FF0000"]- Device: eth0 -----------------------------------------------------------------
Type: Wired
Driver: r8169
State: unavailable[/COLOR]
Default: no
HW Address: 5C:07:71:58:62:3D

Capabilities:
Carrier Detect: yes

Wired Properties
Carrier: off


[COLOR="#FF0000"]- Device: wlan0 [ROUTE NET ] ---------------------------------------------------
Type: 802.11 WiFi
Driver: wl
State: connected
Default: yes[/COLOR]
HW Address: B8:76:3F:C0:28:89
So we see these readings for your connected wireless. Are we trying to troubleshoot wired or wireless? Or does the slow connection persist in both? 

I'm a bit confused.


------------------------------------------------------------

Note to Chili: whois 110.93.194.19

---

### Post by shamsat on 2014-04-04
I tried the both and are the same slow connection.

---

### Post by philinux on 2014-04-04
Connect wired and disconnect wireless and repeat those above commands. Cheers

---

### Post by chili555 on 2014-04-04
I think it is a problem with your internet service provider. Here is the result when you pinged Google:> # ping -c3 [www.google.com](www.google.com)
PING [www.google.com](www.google.com) (110.93.194.19) 56(84) bytes of data.
64 bytes from [www.google.com](www.google.com) (110.93.194.19): icmp_seq=1 ttl=58 time=40.4 ms
64 bytes from [www.google.com](www.google.com) (110.93.194.19): icmp_seq=2 ttl=58 time=42.3 ms
64 bytes from [www.google.com](www.google.com) (110.93.194.19): icmp_seq=3 ttl=58 time=41.0 ms
Here is the result from *whois*:> $ whois 110.93.194.19
% [whois.apnic.net]
% Whois data copyright terms    [http://www.apnic.net/db/dbcopyright.html](http://www.apnic.net/db/dbcopyright.html)

% Information related to '110.93.192.0 - 110.93.255.255'

inetnum:        110.93.192.0 - 110.93.255.255
netname:        TWA
descr:          Transworld Associates (Pvt.) Ltd.
descr:          6th Floor, Executive Tower, Dolmen City
descr:          Marine Drive, Clifton Block 4
descr:          Karachi, Pakistan
country:        PK
admin-c:        TM701-AP
tech-c:         TM701-AP
When I ping Google,I see:> $ ping -c3 [www.google.com](www.google.com)
PING [www.google.com](www.google.com) (74.125.228.243) 56(84) bytes of data.
64 bytes from iad23s24-in-f19.1e100.net (74.125.228.243): icmp_seq=1 ttl=50 time=38.4 ms
64 bytes from iad23s24-in-f19.1e100.net (74.125.228.243): icmp_seq=2 ttl=50 time=37.8 ms
64 bytes from iad23s24-in-f19.1e100.net (74.125.228.243): icmp_seq=3 ttl=50 time=298 ms

--- [www.google.com](www.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 37.886/125.034/298.785/122.860 ms
chili@Think410:~$ whois 74.125.228.243

#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: [https://www.arin.net/whois_tou.html](https://www.arin.net/whois_tou.html)
#


#
# The following results may also be obtained via:
# [http://whois.arin.net/rest/nets;q=74.125.228.243?showDetails=true&showARIN=false&ext=netref2](http://whois.arin.net/rest/nets;q=74.125.228.243?showDetails=true&showARIN=false&ext=netref2)
#

NetRange:       74.125.0.0 - 74.125.255.255
CIDR:           74.125.0.0/16
OriginAS:       
NetName:        GOOGLE
NetHandle:      NET-74-125-0-0-1
Parent:         NET-74-0-0-0-0
NetType:        Direct Allocation
RegDate:        2007-03-13
Updated:        2012-02-24
Ref:            [http://whois.arin.net/rest/net/NET-74-125-0-0-1](http://whois.arin.net/rest/net/NET-74-125-0-0-1)


OrgName:        Google Inc.
OrgId:          GOGL
Address:        1600 Amphitheatre Parkway
City:           Mountain View
StateProv:      CA
PostalCode:     94043
Country:        US
In other words, your search to Google, and I assume all other searches, are re-routed to TWA. When I search for Google, I get Google.

I don't know what is happening, but I am pretty certain the slowdown lies elsewhere than Ubuntu 14.04.

---

