---
title: "error ntpdate[714]: name server cannot be used"
date: 2018-07-04
forum: Networking &amp; Wireless
---

### Post by arapaho on 2018-07-04
I have errors on Kubuntu 16.04. I use cable internet, no VPN. Connection is established automatically. I have no knowledge about networking at all. 

```
lip 04 11:54:18 ntpdate[714]: name server cannot be used: Temporary failure in name resolution (-3)
lip 04 11:54:19 NetworkManager[735]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
```

```
[FONT=monospace][COLOR=#000000]systemd-analyze critical-chain[/COLOR]
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @12.369s
&#9492;&#9472;multi-user.target @12.369s
  &#9492;&#9472;[COLOR=#FF5454]**smbd.service @12.073s +295ms**[/COLOR]
    &#9492;&#9472;[COLOR=#FF5454]**nmbd.service @11.298s +760ms**[/COLOR]
      &#9492;&#9472;network-online.target @11.284s
        &#9492;&#9472;[COLOR=#FF5454]**NetworkManager-wait-online.service @2.454s +8.829s**[/COLOR]
          &#9492;&#9472;[COLOR=#FF5454]**NetworkManager.service @2.129s +308ms**[/COLOR]
[/FONT]
```

```
[FONT=monospace][COLOR=#000000]systemd-analyze blame[/COLOR]
          8.829s [B]NetworkManager-wait-online.service
[/B]          1.491s plymouth-start.service
           922ms networking.service
           794ms dev-sda1.device
           760ms nmbd.service
           742ms winbind.service
           720ms plymouth-read-write.service
           621ms samba-ad-dc.service
           449ms ufw.service
           333ms accounts-daemon.service
           329ms grub-common.service
           308ms NetworkManager.service

[/FONT]
```

I found this
[https://askubuntu.com/questions/775372/ntp-without-dns](https://askubuntu.com/questions/775372/ntp-without-dns)
where somebody reported similar problem and I edited /etc/default/ntpdate and changed yes to no.
```
NTPDATE_USE_NTP_CONF=no
```
but no result.

There is a bug report but looks like nobody care to solve it
[https://bugs.launchpad.net/network-manager/+bug/1568560](https://bugs.launchpad.net/network-manager/+bug/1568560)

---

### Post by whistl034 on 2018-07-08
from the error message, I'm wondering if it's a DNS issue.  Can you browse anywhere successfully?  What happens when you run 'host google.com' ? For that matter, what happens when you run "host whatever.ntp.hostname.you.tried"? 

I just read that since 16.04, Ubuntu has been updated to use systemd-timesyncd instead of ntpd and ntpdate.  What do you get when you run "timedatectl"?

---

### Post by arapaho on 2018-07-08
```
timedatectl      Local time: no 2018-07-08 08:58:59 CEST
  Universal time: no 2018-07-08 06:58:59 UTC
        RTC time: no 2018-07-08 06:58:59
       Time zone: Europe/Warsaw (CEST, +0200)
 Network time on: yes
NTP synchronized: yes
 RTC in local TZ: no


host google.com
google.com has address 172.217.16.46
google.com has IPv6 address 2a00:1450:401b:805::200e
google.com mail is handled by 10 aspmx.l.google.com.
google.com mail is handled by 40 alt3.aspmx.l.google.com.
google.com mail is handled by 20 alt1.aspmx.l.google.com.
google.com mail is handled by 30 alt2.aspmx.l.google.com.
google.com mail is handled by 50 alt4.aspmx.l.google.com.




host whatever.ntp.hostname.you.tried
Host whatever.ntp.hostname.you.tried not found: 3(NXDOMAIN)
```

I was thinking about installing NetworkManager from github
[https://github.com/NetworkManager/NetworkManager](https://github.com/NetworkManager/NetworkManager)
but neither [COLOR=#333333][FONT=Ubuntu]make or autogen.sh starts. I don't know how to do it.

[/FONT][/COLOR]I disabled wait-online 
```
sudo systemctl disable NetworkManager-wait-online.service
```

but I still get
```
journalctl -b -p 3
ntpdate[714]: name server cannot be used: Temporary failure in name resolution (-3)
NetworkManager[735]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
```

---

### Post by whistl034 on 2018-07-11
It looks like you don't actually need ntpdate to synchronize your system clock to an NTP server, as timedatectl shows your systemd-timesyncd has already done that. I would remove ntpdate (sudo apt-get remove ntpdate) and try again. That should eliminate the ntpdate error message.

As for the network manager error, unless you are experiencing network errors, I'd just ignore it.  My Ubuntu 16.04 VM gets that error too. It's not an indication that anything is actually wrong.

```

$ sudo journalctl -b -p 3 | head
-- Logs begin at Wed 2018-07-11 01:25:06 EDT, end at Wed 2018-07-11 01:30:50 EDT. --
Jul 11 01:25:09 ubuntu1604 NetworkManager[755]: nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed

```

---

