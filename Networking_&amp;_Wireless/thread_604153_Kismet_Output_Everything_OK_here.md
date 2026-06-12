---
title: "Kismet Output: Everything OK here?"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by j2p2f2 on 2007-11-05
I'm trying to get Kismet to work and I think I got it, but im not sure. Im using an Atheros AR5211 wireless card built in to my laptop with the madwifi drivers

my source=madwifi_ab,wifi0,atheros

When I run sudo kismet, i get the following

```


default@default-laptop:~$ sudo -s
[sudo] password for default:
root@default-laptop:~# kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (ath0): Enabling monitor mode for madwifi_ab source interface wifi0 channel 6...
WARNING:  Found a non-master non-monitor VAP wifi0::ath0.  Madwifi-ng has historically had problems with normal-mode VAPs combined with monitor-mode VAPs.  You may need to remove them.
NOTICE:  Created Madwifi-NG RFMON VAP kis0
WARNING: wifi0 appears to be using Madwifi-NG.  Some versions of the Madwifi-NG drivers have problems in monitor mode, especially if non-monitor VAPs are active.  If you experience problems, be sure to try the latest versions of Madwifi-NG and remove other VAPs
Source 0 (ath0): Opening madwifi_ab source interface kis0...
Allowing clients to fetch WEP keys.
WARNING:  Disabling GPS logging.
Logging networks to /var/log/kismet/Kismet-Nov-05-2007-1.network
Logging networks in CSV format to /var/log/kismet/Kismet-Nov-05-2007-1.csv
Logging networks in XML format to /var/log/kismet/Kismet-Nov-05-2007-1.xml
Logging cryptographically weak packets to /var/log/kismet/Kismet-Nov-05-2007-1.weak
Logging cisco product information to /var/log/kismet/Kismet-Nov-05-2007-1.cisco
Logging data to /var/log/kismet/Kismet-Nov-05-2007-1.dump
Writing data files to disk every 300 seconds.
Mangling encrypted and fuzzy data packets.
Tracking probe responses and associating probe networks.
Reading AP manufacturer data and defaults from //etc/kismet/ap_manuf
Reading client manufacturer data and defaults from //etc/kismet/client_manuf
Using network-classifier based data encryption detection
Dump file format: wiretap (local code) dump
Crypt file format: airsnort (weak packet) dump
Kismet 2007.01.R1 (Kismet)
Logging data networks CSV XML weak cisco
Listening on port 2501.
Allowing connections from 127.0.0.1/255.255.255.255
Registering builtin client/server protocols...
Registering requested alerts...
Registering builtin timer events...
Gathering packets...
Starting UI...
Looking for startup info from localhost:2501.... found.
Connected to Kismet server 2007.01.R1 on localhost:2501
Reading AP manufacturer data and defaults from //etc/kismet/ap_manuf
Reading client manufacturer data and defaults from //etc/kismet/client_manuf
Killing server...
Didn't detect any Cisco Discovery Packets, unlinking cisco dump
wait: 86: No previous job
Kismet exited.
root@default-laptop:~# Didn't see any weak encryption packets, unlinking weak file
Kismet exiting.

root@default-laptop:~# 


```

Does that look right?

I appear to be getting packets, but my router is listed red (linksys). What does that mean? Also, I receive a lot less packets than I should. 

Wireshark picks up much more packets, but they seem random and not organized. Can anyone help me?

Ive also included a picture :)

[[IMG]http://img136.imageshack.us/img136/7716/screenshotxn9.th.png[/IMG]](http://img136.imageshack.us/my.php?image=screenshotxn9.png)

Thanks for any help!

---

### Post by j2p2f2 on 2007-11-05
Well now its not working for some random reason and i dont know why! Kismet just frustrates me.

---

