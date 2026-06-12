---
title: "WLAN CARD ERRORS on drapper drake"
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by cccc on 2006-09-05
hi

I have wlan card WG311T from Netgear configured with WPA-PSK under drapper drake.
WPA works, but I have a lot of errors:

**ath0** Link encap:Ethernet HWaddr 00:14:6C:31:A1:B3
inet addr:192.168.210.20 Bcast:192.168.200.255 Mask:255.255.255.0
inet6 addr: fe80::214:6cff:fe31:a1b3/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2475 [SIZE="2"]**errors:1940**[/SIZE] dropped:0 overruns:0 frame:651
TX packets:2066 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:200
RX bytes:2858949 (2.7 MiB) TX bytes:310007 (302.7 KiB)
Interrupt:11 Memory:f8a20000-f8a30000

I can post my configurations, but on the same machine I have debian sarge and freeBSD 6.1 installed with exact the same WPA (wpasupplicant) configuration and I don't get any errors.

I think, there is a problem with madwifi driver !
I didn't install any drivers.
my system has seen the wlan card by default.

does anyone get these errors as well ?

---

### Post by lupine_nickt on 2006-09-05
Maybe try updating madwifi? 

xF,

...Nick

---

### Post by cccc on 2006-09-05
you mean, download from:

[http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233](http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233)
[http://svn.madwifi.org/trunk/](http://svn.madwifi.org/trunk/)

and install from source

or where can I find **madwifi repository for ubuntu** ?

---

### Post by lupine_nickt on 2006-09-05
Building from source would do the trick, although I suggest using a published release rather than the CVS source!

xF,

...Nick

---

### Post by cccc on 2006-09-05
> **lupine_nickt said:**
> Building from source would do the trick, although I suggest using a published release rather than the CVS source!

xF,

...Nick

which download url should be correct ?

---

### Post by lupine_nickt on 2006-09-05
[0.9.2](http://prdownloads.sourceforge.net/madwifi/madwifi-0.9.2.tar.gz?download) looks to be the most recent version.

xF,

...Nick

---

### Post by cccc on 2006-09-06
under debian sarge stable installed on the same hardware,
I have madwifi-ng installed and don't have any errors.

I'll try **madwifi-ng** from [http://svn.madwifi.org/trunk](http://svn.madwifi.org/trunk)

---

### Post by cccc on 2006-09-09
probably it's a **BUG ** or an error in the madwifi driver

anyway, I solved this problem:

1.) after fresh installation of the systems, before online updates:```

# apt-get install subversion
# cd /usr/src
# svn checkout http://svn.madwifi.org/trunk madwifi-ng
# cd madwifi-ng
# make clean
# make
# make install
```
2.) install all online updates
3.) restart

wpa_supplicant was not working, so I've done:

4.)```
apt-get remove --purge wpasupplicant
```
5.) download the newest wpa_supplicant from: 
[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)```

# tar xvfz  wpa_supplicant-0.4.9.tar.gz
# cd /wpa_supplicant-0.4.9
```
create **.config** and put into:```

CONFIG_DRIVER_MADWIFI=y
CFLAGS += -I/usr/src/madwifi-ng
CONFIG_CTRL_IFACE=y
``````

# make clean
# make
# make install
```

now I don't get any errors !

greetings
cccc

---

