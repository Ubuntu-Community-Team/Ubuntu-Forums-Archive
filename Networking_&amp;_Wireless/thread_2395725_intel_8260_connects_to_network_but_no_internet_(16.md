---
title: "intel 8260 connects to network but no internet (16.04)"
date: 2018-07-05
forum: Networking &amp; Wireless
---

### Post by gep8888 on 2018-07-05
Hi //
Recently we upgraded our home adsl connection (24mbps) to vdsl (50mbps/*VDSL2 17a profile*) and since almost day-1 i cannot even open google.com...

(1) Wifi always appears connected & sometimes i get a response and can browse but only for very small bursts of time.
(2) i am on a asus fx502vm laptop with dual windows10/ubuntu setup.  Windows have **no speed/connection problems **at all..
(3) i even tried with different modem/router (cheap technicolor replaced with tp-link archer vr2800)

Attached the usual info tidbits from wireless_info script
([https://pastebin.com/a4PWGUt4](https://pastebin.com/a4PWGUt4))
[ATTACH=CONFIG]280290[/ATTACH]

At some point i managed to ping successfully (nslookup google.com also worked in case this could be a dns error) :
```

 ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=25 ttl=57 time=1507 ms
64 bytes from 8.8.8.8: icmp_seq=26 ttl=57 time=483 ms
64 bytes from 8.8.8.8: icmp_seq=27 ttl=57 time=72.4 ms
64 bytes from 8.8.8.8: icmp_seq=28 ttl=57 time=71.0 ms
64 bytes from 8.8.8.8: icmp_seq=29 ttl=57 time=70.8 ms
64 bytes from 8.8.8.8: icmp_seq=30 ttl=57 time=71.3 ms
64 bytes from 8.8.8.8: icmp_seq=31 ttl=57 time=71.3 ms
64 bytes from 8.8.8.8: icmp_seq=32 ttl=57 time=70.9 ms
64 bytes from 8.8.8.8: icmp_seq=33 ttl=57 time=70.6 ms
64 bytes from 8.8.8.8: icmp_seq=34 ttl=57 time=70.3 ms
^C
--- 8.8.8.8 ping statistics ---
38 packets transmitted, 10 received, 73% packet loss, time 37671ms
rtt min/avg/max/mdev = 70.370/255.995/1507.369/434.873 ms, pipe 2
``` 

help:-s

---

### Post by gep8888 on 2018-07-06
a quick list of things i tried today based on several answers around here & didnt work:
 
```
 
sudo service network-manager restart

```
sometimes it restored to a working connection but for very brief time (1-2 minutes max)

```

sudo modprobe -r iwlwifi
sudo modprobe iwlwifi bt_coex-active=0 11n_disable=8|1|0

```
didnt do anything

```

sudo iw reg set GR

```
my region had this generic 00 but didnt change anything (i dont really have wifi wake/sleep reconnect problems.. The connection is stable but not working correctly)

```

sudo mv /lib/firmware/iwlwifi-8000C-36.ucode /lib/firmware/iwlwifi-8000C-36.ucode.BORKED

```
to force another version as suggested in several other threads

also played a little with the default wifi properties of my router (force some combination of b/g/n, bandwidth, etc) with no luck either..

**please** throw me suggestions.. Anything:(

---

