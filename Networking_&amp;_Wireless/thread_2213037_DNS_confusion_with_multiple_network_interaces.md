---
title: "DNS confusion with multiple network interaces"
date: 2014-03-24
forum: Networking &amp; Wireless
---

### Post by mikebordon on 2014-03-24
Hi,

I'm running in an environment where two network interfaces are active at once - ethernet and wireless. My ethernet connection has a DNS to resolve hostnames on our intranet, whereas the wireless connection has access only to the public internet. When connected to both networks I am sometimes unable to resolve intranet hostnames because it appears to be attempting resolution via the wireless interface. As soon as I disable the wireless card works as expected 100% of the time. Any help would be appreciated.

For the record I'm running 13.10, but I've had this problem since I installed 12.10 on this box.

Thanks,

Mike

---

### Post by varunendra on 2014-03-24
Welcome to the forums Mike! :)

Are you sure it is a DNS problem not a routing issue? How have you confirmed that it is a DNS issue?

Assuming you are using Network Manager to control the interfaces, please post the outputs of -
```
nm-tool
route -n
```

Both outputs from both situations - that is - when it works and when it doesn't.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by mikebordon on 2014-03-25
Thanks for the reply.

No, I'm not sure it's a DNS issue. Because pinging a local hostname fails to resolve to an IP, I assumed it was using the wireless interface's DNS and that's it.

Here's out the output you requested:

**Working:**

```

NetworkManager Tool


State: connected (global)


- Device: wlan0  [tacnet] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           no
  HW Address:        00:23:14:D6:93:40


  Capabilities:
    Speed:           18 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    POLLO3:          Infra, C2:9F:DB:55:A9:42, Freq 2412 MHz, Rate 54 Mb/s, Strength 90 WPA WPA2
    POLLO3:          Infra, 06:27:22:F9:47:D5, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    POLLO3:          Infra, 06:27:22:F9:47:4C, Freq 2412 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    ReproductiveWellness: Infra, 48:F8:B3:66:CE:A8, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    tacnet:          Infra, D8:C7:C8:C2:C5:C2, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA2
    Jankovic Agency: Infra, 2C:B0:5D:92:24:D7, Freq 2417 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    Private Network: Infra, 74:D0:2B:8B:BD:C8, Freq 2427 MHz, Rate 54 Mb/s, Strength 59 WPA2
    tacnet:          Infra, D8:C7:C8:C2:C7:A2, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA2
    ReproductiveWellness5: Infra, 48:F8:B3:66:CE:AA, Freq 5765 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    nolongerinuse:   Infra, 74:D0:2B:8B:BD:CC, Freq 5180 MHz, Rate 54 Mb/s, Strength 40 WPA2
    vpequities:      Infra, C8:60:00:E8:AA:E4, Freq 5785 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    NETGEAR43:       Infra, 04:A1:51:87:E7:69, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    POLLO 4.0:       Infra, C6:9F:DB:55:A9:42, Freq 2412 MHz, Rate 54 Mb/s, Strength 87 WEP
    POLLO 4.0:       Infra, 0A:27:22:F9:47:D5, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WEP
    POLLO 4.0:       Infra, 0A:27:22:F9:47:4C, Freq 2412 MHz, Rate 54 Mb/s, Strength 84 WEP
    POLLO 4.0:       Infra, 0A:27:22:F9:47:85, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WEP
    STTC:            Infra, 48:F8:B3:8E:BA:0B, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP
    CPC Strategy Guest: Infra, 0E:27:22:F9:47:D5, Freq 2462 MHz, Rate 54 Mb/s, Strength 84
    CPC Strategy Guest: Infra, 0E:27:22:F9:47:4C, Freq 2412 MHz, Rate 54 Mb/s, Strength 82
    ReproductiveWellness-guest: Infra, 4E:F8:B3:66:CE:A8, Freq 2462 MHz, Rate 54 Mb/s, Strength 70
    CPC Strategy Guest: Infra, CA:9F:DB:55:A9:42, Freq 2412 MHz, Rate 54 Mb/s, Strength 62
    CPC Strategy Guest: Infra, 0E:27:22:F9:47:85, Freq 2437 MHz, Rate 54 Mb/s, Strength 59
    SageCollege:     Infra, 00:17:C5:BF:3E:35, Freq 2447 MHz, Rate 54 Mb/s, Strength 59
    SETUP:           Ad-Hoc, 66:2A:2F:53:7C:99, Freq 2462 MHz, Rate 11 Mb/s, Strength 32
    tacnet:          Infra, D8:C7:C8:C2:C0:52, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA2
    POLLO3:          Infra, 06:27:22:F9:47:85, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    vpequities:      Infra, C8:60:00:E8:AA:E0, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    OverdrivePro35A: Infra, 84:DB:2F:05:43:5A, Freq 2422 MHz, Rate 54 Mb/s, Strength 32 WPA2
    vpequities_5GEXT:Infra, 2A:C6:8E:81:F2:43, Freq 5785 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    tacnet:          Infra, D8:C7:C8:C2:C5:92, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    STTC-guest:      Infra, 02:F8:B3:8E:BA:0C, Freq 2437 MHz, Rate 54 Mb/s, Strength 35
    *tacnet:         Infra, D8:C7:C8:C2:BE:A2, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA2


  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.225
    DNS:             209.242.128.101




- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        5C:FF:35:09:A1:6F


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         172.22.30.108
    Prefix:          22 (255.255.252.0)
    Gateway:         172.22.28.1


    DNS:             10.1.111.151

```

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.22.28.1     0.0.0.0         UG    0      0        0 eth0
172.22.28.0     0.0.0.0         255.255.252.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

```

**Not Working:**

```
NetworkManager Tool


State: connected (global)


- Device: wlan0  [tacnet] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           no
  HW Address:        00:23:14:D6:93:40


  Capabilities:
    Speed:           18 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    POLLO3:          Infra, C2:9F:DB:55:A9:42, Freq 2412 MHz, Rate 54 Mb/s, Strength 90 WPA WPA2
    POLLO3:          Infra, 06:27:22:F9:47:D5, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    POLLO3:          Infra, 06:27:22:F9:47:4C, Freq 2412 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    ReproductiveWellness: Infra, 48:F8:B3:66:CE:A8, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    tacnet:          Infra, D8:C7:C8:C2:C5:C2, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA2
    Jankovic Agency: Infra, 2C:B0:5D:92:24:D7, Freq 2417 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    Private Network: Infra, 74:D0:2B:8B:BD:C8, Freq 2427 MHz, Rate 54 Mb/s, Strength 59 WPA2
    tacnet:          Infra, D8:C7:C8:C2:C7:A2, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA2
    ReproductiveWellness5: Infra, 48:F8:B3:66:CE:AA, Freq 5765 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    nolongerinuse:   Infra, 74:D0:2B:8B:BD:CC, Freq 5180 MHz, Rate 54 Mb/s, Strength 40 WPA2
    vpequities:      Infra, C8:60:00:E8:AA:E4, Freq 5785 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    NETGEAR43:       Infra, 04:A1:51:87:E7:69, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    POLLO 4.0:       Infra, C6:9F:DB:55:A9:42, Freq 2412 MHz, Rate 54 Mb/s, Strength 87 WEP
    POLLO 4.0:       Infra, 0A:27:22:F9:47:D5, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WEP
    POLLO 4.0:       Infra, 0A:27:22:F9:47:4C, Freq 2412 MHz, Rate 54 Mb/s, Strength 84 WEP
    POLLO 4.0:       Infra, 0A:27:22:F9:47:85, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WEP
    STTC:            Infra, 48:F8:B3:8E:BA:0B, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP
    CPC Strategy Guest: Infra, 0E:27:22:F9:47:D5, Freq 2462 MHz, Rate 54 Mb/s, Strength 84
    CPC Strategy Guest: Infra, 0E:27:22:F9:47:4C, Freq 2412 MHz, Rate 54 Mb/s, Strength 82
    ReproductiveWellness-guest: Infra, 4E:F8:B3:66:CE:A8, Freq 2462 MHz, Rate 54 Mb/s, Strength 70
    CPC Strategy Guest: Infra, CA:9F:DB:55:A9:42, Freq 2412 MHz, Rate 54 Mb/s, Strength 62
    CPC Strategy Guest: Infra, 0E:27:22:F9:47:85, Freq 2437 MHz, Rate 54 Mb/s, Strength 59
    SageCollege:     Infra, 00:17:C5:BF:3E:35, Freq 2447 MHz, Rate 54 Mb/s, Strength 59
    SETUP:           Ad-Hoc, 66:2A:2F:53:7C:99, Freq 2462 MHz, Rate 11 Mb/s, Strength 32
    tacnet:          Infra, D8:C7:C8:C2:C0:52, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA2
    POLLO3:          Infra, 06:27:22:F9:47:85, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    vpequities:      Infra, C8:60:00:E8:AA:E0, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    OverdrivePro35A: Infra, 84:DB:2F:05:43:5A, Freq 2422 MHz, Rate 54 Mb/s, Strength 32 WPA2
    vpequities_5GEXT:Infra, 2A:C6:8E:81:F2:43, Freq 5785 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    tacnet:          Infra, D8:C7:C8:C2:C5:92, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    STTC-guest:      Infra, 02:F8:B3:8E:BA:0C, Freq 2437 MHz, Rate 54 Mb/s, Strength 35
    *tacnet:         Infra, D8:C7:C8:C2:BE:A2, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA2


  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.225
    DNS:             209.242.128.101




- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        5C:FF:35:09:A1:6F


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         172.22.30.108
    Prefix:          22 (255.255.252.0)
    Gateway:         172.22.28.1


    DNS:             10.1.111.151

```

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.22.28.1     0.0.0.0         UG    0      0        0 eth0
172.22.28.0     0.0.0.0         255.255.252.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

```

There's no noticeable difference, but I think it "worked" because the resolved IP was cached from when I disconnected the wireless network, thus skipping hostname resolution. If there's a way to "flush" the cache, then I can try that and run the commands again, but I guess there's no guarantee that'll ever "work."

Thanks again for your help.

Mike

---

### Post by mikebordon on 2014-03-25
Just a bit more information. I ran "host -v jira" with it working and not, and the following are the results:

Working
```

Trying "jira.replaced-domain.com"
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 14315
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0


;; QUESTION SECTION:
;jira.replaced-domain.com.	IN	A


;; ANSWER SECTION:
jira.replaced-domain.com. 849	IN	A	172.22.29.24


Received 60 bytes from 127.0.1.1#53 in 1 ms
Trying "jira.replaced-domain.com"
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 1554
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0


;; QUESTION SECTION:
;jira.replaced-domain.com.	IN	AAAA


;; AUTHORITY SECTION:
replaced-domain.com.	900	IN	SOA	dc1.replaced-domain.com. hostmaster.replaced-domain.com. 6708 900 600 86400 3600


Received 95 bytes from 127.0.1.1#53 in 2 ms
Trying "jira.replaced-domain.com"
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 19692
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0


;; QUESTION SECTION:
;jira.replaced-domain.com.	IN	MX


;; AUTHORITY SECTION:
replaced-domain.com.	900	IN	SOA	dc1.replaced-domain.com. hostmaster.replaced-domain.com. 6708 900 600 86400 3600


Received 95 bytes from 127.0.1.1#53 in 2 ms

```

Not Working
```

Trying "jira.replaced-domain.com"
Trying "jira"
Host jira not found: 3(NXDOMAIN)
Received 97 bytes from 127.0.1.1#53 in 133 ms

```

This is where my understanding is a bit lacking. Is there some kind of service running locally on 127.0.1.1 that is responsible for routing lookup requests to the DNS?

Mike

---

### Post by sandyd on 2014-03-25
Could be the dnsmasq cache.
See [http://askubuntu.com/questions/233222/how-can-i-disable-the-dns-that-network-manager-uses](http://askubuntu.com/questions/233222/how-can-i-disable-the-dns-that-network-manager-uses) for instructions on how to disable

---

### Post by mikebordon on 2014-03-25
> **sandyd said:**
> Could be the dnsmasq cache.
See [http://askubuntu.com/questions/233222/how-can-i-disable-the-dns-that-network-manager-uses](http://askubuntu.com/questions/233222/how-can-i-disable-the-dns-that-network-manager-uses) for instructions on how to disable

So far so good, but I'll monitor it for the next day or so. Would this be an ultimate solution? In other words, do I lose any noticeable functionality with dnsmasq disabled?

Thanks again.

Mike

---

### Post by varunendra on 2014-03-25
The dnsmasq is just an alternative (newer) method of DNS resolution. If you disable it, NetworkManager would simply fall back to the older method of using the "/etc/resolv.conf" file which is fine.

In short - no, you shouldn't lose any functionality and this should be permanent.
*(Not sure if an update to "resolvconf" package may re-enable it in NetworkManager though. Sometimes people who prefer the older method simply purge the "resolvconf" package altogether)*

---

### Post by SeijiSensei on 2014-03-26
You can force the choice of nameservers in /etc/network/interfaces.  If you are using static addressing for the LAN connection, try adding this line to end of the eth0 stanza in that file:
```
dns-nameserver 1.2.3.4 5.6.7.8
```
with the appropriate IP addresses of the servers you wish to use.

Another option is to edit the file /etc/resolvconf/resolv.conf.d/head and add the nameservers you want to use there.  That's been my solution for a while now:
```

nameserver 1.2.3.4
nameserver 5.6.7.8

```
These will be placed above the default 127.0.1.1 address that Ubuntu automatically generates via resolvconf.

---

### Post by mikebordon on 2014-03-26
Thanks, Seiji, but I don't have an eth0 stanza in /etc/network/interfaces, and /etc/resolvconf/resolvconf.d/head is empty and has a big disclaimer not to edit the file by hand because it'll be overwritten (although it sounds like you're suggesting that it won't).

Either way, everything is still working with dnsmasq disabled, and with no noticeable side effects, so I'm happy with the solution.

I appreciate all the replies. Thanks so much for the help.

Mike

---

### Post by varunendra on 2014-03-26
Yes, your current solution is good enough. Just to make it clear, the contents of the file "etc/resolvconf/resolv.conf.d/head" are printed exactly 'As-it-is' at the 'Head' of "/etc/resolv.conf" file.

As such the comment you saw is an information meant for those who try to manually edit the "/etc/resolv.conf" file directly (the traditional way), which will be overwritten by the contents of the "etc/resolvconf/resolv.conf.d/head" file if "resolvconf" package is installed and the "dnsmasq" method is being used by Network Manager. So the solution that SeijiSensei suggested is equally solid. :)

---

