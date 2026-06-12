---
title: "Intermittent Connection/Packet Loss - Intel 3160 AC [Ubuntu 16.10]"
date: 2018-01-31
forum: Networking &amp; Wireless
---

### Post by archy-bold on 2018-01-31
I'm having trouble connecting to a specific wifi network, I can connect to all others without issue. Unfortunately I can't really make changes to the network/router itself as it's a corporate one.

My issue is basically that I can connect to the network but the connection is intermittent and if I run ping I get one of the following:

```
$ ping google.co.uk
ping: google.co.uk: Temporary failure in name resolution

```

or:

```
$ ping google.co.ukPING google.co.uk (216.58.206.67) 56(84) bytes of data.
64 bytes from lhr35s11-in-f3.1e100.net (216.58.206.67): icmp_seq=1 ttl=50 time=8.41 ms
64 bytes from lhr35s11-in-f3.1e100.net (216.58.206.67): icmp_seq=2 ttl=50 time=9.19 ms
64 bytes from lhr35s11-in-f3.1e100.net (216.58.206.67): icmp_seq=3 ttl=50 time=8.96 ms
64 bytes from lhr35s11-in-f3.1e100.net (216.58.206.67): icmp_seq=4 ttl=50 time=13.8 ms
64 bytes from lhr35s11-in-f3.1e100.net (216.58.206.67): icmp_seq=5 ttl=50 time=51.6 ms
64 bytes from lhr35s11-in-f3.1e100.net (216.58.206.67): icmp_seq=6 ttl=50 time=9.28 ms
64 bytes from lhr35s11-in-f3.1e100.net (216.58.206.67): icmp_seq=7 ttl=50 time=9.15 ms
64 bytes from lhr35s11-in-f3.1e100.net (216.58.206.67): icmp_seq=8 ttl=50 time=9.23 ms
64 bytes from lhr35s11-in-f3.1e100.net (216.58.206.67): icmp_seq=9 ttl=50 time=9.20 ms
64 bytes from lhr35s11-in-f3.1e100.net (216.58.206.67): icmp_seq=10 ttl=50 time=8.76 ms
^C
--- google.co.uk ping statistics ---
14 packets transmitted, 10 received, 28% packet loss, time 13088ms
rtt min/avg/max/mdev = 8.418/13.772/51.616/12.700 ms
```

I'm using an Intel Wireless 3160 AC (rev 83) wireless adapter using the iwlwifi driver.

I've found numerous threads with similar issues and have tried the following to try to rectify the problem:
[LIST=1]
[*]Updated the firmware to 1.170 (this seemed to initially solve the problem, but the issue returned)
[*]Turned off wifi Power Management
[*]Disabled 11n in the iwlwifi options
[*]Additionally disabled power_save and bluetooth co-exist options in iwlwifi
[*]Set region with ```
sudo iw reg set GB
```
[/LIST]

Here's the dump from wireless-info: [https://paste.ubuntu.com/26495631/](https://paste.ubuntu.com/26495631/)

Thanks

---

### Post by chili555 on 2018-01-31
Please note: [http://fridge.ubuntu.com/2017/07/20/ubuntu-16-10-yakkety-yak-end-of-life-reached-on-july-20-2017/](http://fridge.ubuntu.com/2017/07/20/ubuntu-16-10-yakkety-yak-end-of-life-reached-on-july-20-2017/)

After you update, you will probably see the same things in your logs:> [ 4583.754540] wlp1s0: RX AssocResp from <MAC '13 Fielden' [AC14]> (capab=0x411 status=0 aid=3)
[ 4583.755040] wlp1s0: associated
[ 5761.591725] wlp1s0: deauthenticating from <MAC '13 Fielden' [AC14]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 5763.801902] wlp1s0: authenticate with <MAC 'COLONY_Member' [AC11]>
[ 5763.803892] wlp1s0: send auth to <MAC 'COLONY_Member' [AC11]> (try 1/3)
[ 5763.804933] wlp1s0: authenticated
[ 5763.807697] wlp1s0: associate with <MAC 'COLONY_Member' [AC11]> (try 1/3)
[ 5763.809660] wlp1s0: RX AssocResp from <MAC 'COLONY_Member' [AC11]> (capab=0x11 status=0 aid=20)
[ 5763.812686] wlp1s0: associated
[ 5763.861840] wlp1s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'COLONY_Member' [AC11]>
[ 5768.133441] wlp1s0: disconnect from AP <MAC 'COLONY_Member' [AC11]> for new auth to <MAC 'COLONY_Member' [AC5]>
[ 5768.136282] wlp1s0: authenticate with <MAC 'COLONY_Member' [AC5]>
[ 5768.139911] wlp1s0: send auth to <MAC 'COLONY_Member' [AC5]> (try 1/3)
[ 5768.242765] wlp1s0: send auth to <MAC 'COLONY_Member' [AC5]> (try 2/3)
[ 5768.244733] wlp1s0: authenticated
[ 5768.246691] wlp1s0: associate with <MAC 'COLONY_Member' [AC5]> (try 1/3)
[ 5768.249700] wlp1s0: RX AssocResp from <MAC 'COLONY_Member' [AC5]> (capab=0x431 status=0 aid=8)
[ 5768.261458] wlp1s0: associated
Your wireless is roaming and dropping more or less continuously from access point to another access point looking for a better connection. Sort of reminds me of an old girlfriend!

I suggest that you try binding Network Manager to the strongest of these like this: [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

...after you upgrade, of course.

---

### Post by archy-bold on 2018-02-01
Heh, yeah, I've been putting off updating as I want to get an LTS release.

But yeah, you're absolutely right, it's surrounded by access points and struggling to choose one. Nary a problem since fixing the access point address.

I might write a script to determine the best signal and automatically set that.

---

### Post by archy-bold on 2018-02-01
Ok, I've written a bash script that will check the strengths of any found access points for the given network SSID and ask if you want to update the setting to its MAC address. This would be useful if you move around a lot and want to ensure you have the strongest signal.

Usage: ./set-access-points.sh [network SSID] [network interface id = wlan0]

[https://gist.github.com/archy-bold/9a4cdee49309e4a2d059c900362fa9dc](https://gist.github.com/archy-bold/9a4cdee49309e4a2d059c900362fa9dc)

---

