---
title: "ipw2200 ver 1.0.6 in feisty problems"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by afrodocter on 2007-08-22
the feisty stock drivers work but i would like to use the ipw2200 1.0.6 drivers in so that i can use my card with kismet and other wireless utils. i dont care about wpa at the momment.

i read and followed this howto.
[http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)

non of the remove old scrpits worked. i reset the /bin/sh to point at /bin/bash instead of dash. the remove-old scripts now run but dont seem to be written correctly.

here is the output the ieee80211-1.0.3 remove-old script


```

root@tosh:/usr/local/src/new_ipw2200/ieee80211-1.0.3# sh remove-old 
Checking in /lib/modules/2.6.20-15-generic/ for ieee80211 components...

/lib/modules/2.6.20-15-generic/kernel/ubuntu/net/rtl_ieee80211/ieee80211-rtl.ko
/lib/modules/2.6.20-15-generic/kernel/net/ieee80211
/lib/modules/2.6.20-15-generic/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.20-15-generic/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.20-15-generic/kernel/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.20-15-generic/kernel/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.20-15-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko
/lib/modules/2.6.20-15-generic/kernel/net/ieee80211/ieee80211.ko

Above files found.  Remove? [y],n 
grep: /lib/modules/2.6.20-15-generic//.config: No such file or directory
grep: /lib/modules/2.6.20-15-generic//include/linux/autoconf.h: No such file or directory
root@tosh:/usr/local/src/new_ipw2200/ieee80211-1.0.3# 

```

i think the use of $KERN is incorrect in some spots of the remove-old script and should add /build, i have not edited the script so that we can isolate the problem.

thanks for the help
alex

---

### Post by Roswellgrey on 2007-08-22
I know this is not answering your question, but I have an 2200BG in a Tosh laptop , totally stock drivers from the Feisty install ( driver=ipw2200 driverversion=1.2.0), and Kismet works just fine .....

---

### Post by afrodocter on 2007-08-22
how did you determine your driver version. i thought that i read stock feisty had a <1.0 ipw2200 driver. my kernel is 2.6.20-15-generic.

---

### Post by afrodocter on 2007-08-22
here is my error when i start up kismet. maybe i am barking up the wrong tree? 
```

root@tosh:~# kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (inter_card): Enabling monitor mode for ipw2200 source interface eth1 channel 6...
Source 0 (inter_card): Opening ipw2200 source interface eth1...
Allowing clients to fetch WEP keys.
WARNING:  Disabling GPS logging.
Logging networks to /var/log/kismet/Kismet-Aug-22-2007-1.network
Logging networks in CSV format to /var/log/kismet/Kismet-Aug-22-2007-1.csv
Logging networks in XML format to /var/log/kismet/Kismet-Aug-22-2007-1.xml
Logging cryptographically weak packets to /var/log/kismet/Kismet-Aug-22-2007-1.weak
Logging cisco product information to /var/log/kismet/Kismet-Aug-22-2007-1.cisco
Logging data to /var/log/kismet/Kismet-Aug-22-2007-1.dump
Writing data files to disk every 300 seconds.
Mangling encrypted and fuzzy data packets.
Tracking probe responses and associating probe networks.
Reading AP manufacturer data and defaults from //etc/kismet/ap_manuf
Reading client manufacturer data and defaults from //etc/kismet/client_manuf
Using network-classifier based data encryption detection
Dump file format: wiretap (local code) dump
Crypt file format: airsnort (weak packet) dump
Kismet 2006.04.R1 (Kismet)
Logging data networks CSV XML weak cisco
Listening on port 2501.
Allowing connections from 127.0.0.1/255.255.255.255
Failed to set up UI server: TcpServer bind() failed: Cannot assign requested address
Didn't detect any networks, unlinking network list.
Didn't detect any networks, unlinking CSV network list.
Didn't detect any networks, unlinking XML network list.
Didn't detect any Cisco Discovery Packets, unlinking cisco dump
Didn't capture any packets, unlinking dump file
Didn't see any weak encryption packets, unlinking weak file
WARNING: Sometimes cards don't always come out of monitor mode
         cleanly.  If your card is not fully working, you may need to
         restart or reconfigure it for normal operation.
Kismet exiting.
root@tosh:~# 

```

---

### Post by Roswellgrey on 2007-08-22
> **afrodocter said:**
> how did you determine your driver version. i thought that i read stock feisty had a <1.0 ipw2200 driver. my kernel is 2.6.20-15-generic.

I must admit that I allowed the UpdateManager's suggested updates immediately after install, so I am running the auto-updated stock Feisty :)  
As such, I am running kernel 2.6.20.16-generic.
I haven't *manually* updated / changed anything , though . 

"lshw -class network"  shows the driver version in the "configuration" line ...

My Kismet startup is identical to yours until this bit ...

```
Allowing connections from 127.0.0.1/255.255.255.255
Registering builtin client/server protocols...
Registering requested alerts...
Registering builtin timer events...
Gathering packets...
Starting UI...
Looking for startup info from localhost:2501.... found.
Connected to Kismet server 2006.04.R1 on localhost:2501
Reading AP manufacturer data and defaults from //etc/kismet/ap_manuf
Reading client manufacturer data and defaults from //etc/kismet/client_manuf

```

That is, it doesn't bomb out with the UI Server error. 

To me, it looks like it has opened the capture device OK, and this is some form of User Interface problem ( local ip config, permissions ? )  but I am only guessing ...

Edit : some quite old, but maybe valid, ideas here ( about 3/4 way down regading /etc/hosts file )
-> [http://wiki.wirelessleiden.nl/moin.cgi/KisMet](http://wiki.wirelessleiden.nl/moin.cgi/KisMet)

---

### Post by afrodocter on 2007-08-22
from reading the section you recomended i tried 
```

ifconfig lo 127.0.0.1 

```

and now my kismet works perfectly. thanks for your suggestions. its weird that ubuntu does not assign lo this address by default correct? i thought this was essential for many utils and services.

---

### Post by Roswellgrey on 2007-08-23
As I understand it, "lo" exists due to the presence of 

[I]auto lo
iface lo inet loopback[/I]

in /etc/network/interfaces  (and this is part of the default file)

You might also want to check that

*127.0.0.1       localhost*

is in /etc/hosts


Any chance these lines have been removed ?
If they are still there, it might be worth a look at "dmesg"  , and see if it gives a clue why this interface isn't being created.

Anyways, glad you got it working :)

---

### Post by afrodocter on 2007-08-24
you are right. i had removed the /etc/network/interfaces file so that NetworkManager would manage my devices (because i had manually configured them) and i didnt realize lo was setup as well. 

thanks for the help

---

