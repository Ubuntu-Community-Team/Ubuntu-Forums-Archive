---
title: "KNetworkmanager doesnt show wireless networks"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by itkejser on 2008-01-27
Hi Everyone.

I have a compaq nx7010 running kubuntu 7.10 (Gutsy gibbon) with a ipw2200 wireless chipset. I can successfully run iwlist and make a scan that shows to wireless networks around me. But for some reason KNnetworkmanager does not show any wireless networks. Any help is much appreciated.

Regards Troels

---

### Post by itkejser on 2008-01-28
iwlist gives the following output:
martin@lankubt050:~$ iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:0B:AC:E6:B5:4C
                    ESSID:"Lanoe Wifinet"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=89/100  Signal level=-40 dBm
                    Extra: Last beacon: 2320ms ago
So it looks like the driver is correctly loaded right?

---

### Post by Captain_Redbeard on 2008-01-28
I'm having the same problem.

Or actually, I've been investigating this a bit. It seems that on a fresh install it does list the wireless networks. But once I have clicked "manual configuration" they all disappear and the right-click menu no longer lists the wireless networks, further more there doesn't seem to be a way to get them back. It is very frustrating and I have no clue how to fix it. I've been trying to fins any config files for knetworkmanager to delete them as well, but without any success....

---

### Post by itkejser on 2008-01-28
Captain read this thread. And delete the entries in the config file.
[https://answers.launchpad.net/ubuntu/+source/knetworkmanager/+question/5327](https://answers.launchpad.net/ubuntu/+source/knetworkmanager/+question/5327)
I can now see all the wireless networks present. Still no cigar though, no traffic passes. The interface pickup a dhcp address from the router, but no traffic passes, hmm

---

