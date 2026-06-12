---
title: "help with kismet"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by miatawnt2b on 2008-07-31
I dl'ed and compiled the latest stable kismet on my 7.10 laptop.  It's using the ipw2200 wireless driver, so I edited the kismet.conf to reflect.  When I 'sudo kismet' I get an error that it can't connect to localhost:2501.  The exact text is below.  Can someone help?
Thanks!
-J

```
Launching kismet_server: /usr/local/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (wireless): Enabling monitor mode for ipw2200 source interface eth1 channel 6...
Source 0 (wireless): Opening ipw2200 source interface eth1...
Will attempt to put networkmanager to sleep...
Allowing clients to fetch WEP keys.
SSID cloak file did not exist, it will be created.
IP track file did not exist, it will be created.
Logging networks to Kismet-Jul-31-2008-8.network
Logging networks in CSV format to Kismet-Jul-31-2008-8.csv
Logging networks in XML format to Kismet-Jul-31-2008-8.xml
Logging cryptographically weak packets to Kismet-Jul-31-2008-8.weak
Logging cisco product information to Kismet-Jul-31-2008-8.cisco
Logging gps coordinates to Kismet-Jul-31-2008-8.gps
Logging data to Kismet-Jul-31-2008-8.dump
Writing data files to disk every 300 seconds.
Mangling encrypted and fuzzy data packets.
Tracking probe responses and associating probe networks.
Reading AP manufacturer data and defaults from /usr/local/etc/ap_manuf
Reading client manufacturer data and defaults from /usr/local/etc/client_manuf
Using network-classifier based data encryption detection
Not tracking duplicate IVs
Putting networkmanager to sleep...
Dump file format: wiretap (local code) dump
Crypt file format: airsnort (weak packet) dump
Kismet 2008.05.R1 (Kismet)
Logging data networks CSV XML weak cisco gps
GPSD cannot connect: Connection refused
Listening on port 2501.
Allowing connections from 127.0.0.1/255.255.255.255
Registering builtin client/server protocols...
Registering requested alerts...
Registering builtin timer events...
Gathering packets...
Launching kismet_client: /usr/local/bin/kismet_client
Launched client, pid 11946
FATAL:  Could not connect to localhost:2501.
Didn't see any weak encryption packets, unlinking weak file
WARNING: Sometimes cards don't always come out of monitor mode
         cleanly.  If your card is not fully working, you may need to
         restart or reconfigure it for normal operation.
Trying to wake networkmanager back up...
Kismet exiting.
Done.

```

---

