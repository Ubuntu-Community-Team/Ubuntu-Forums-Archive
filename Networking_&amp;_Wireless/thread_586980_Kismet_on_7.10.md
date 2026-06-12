---
title: "Kismet on 7.10"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by rleechb on 2007-10-22
I'm having a bit of trouble getting kismet to function correctly.  I'm running an atheros-based  card and putting wifi0 in monitor mode via airmon-ng. The problem is, after the kismet GUI pops up, I don't see any 802.11 traffic at all.  My kismet.conf is as follows:

# Version of Kismet config
version=2005.06.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
suiduser=rlee

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=madwifi_ag,wifi0,AtherosAG

Here's also a little bit @ the CLI:

```
root@goooh:/etc/kismet# kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (AtherosAG): Enabling monitor mode for madwifi_ag source interface wifi0 channel 6...
WARNING:  Found a non-master non-monitor VAP wifi0::ath0.  Madwifi-ng has historically had problems with normal-mode VAPs combined with monitor-mode VAPs.  You may need to remove them.
NOTICE:  Created Madwifi-NG RFMON VAP kis0
WARNING: wifi0 appears to be using Madwifi-NG.  Some versions of the Madwifi-NG drivers have problems in monitor mode, especially if non-monitor VAPs are active.  If you experience problems, be sure to try the latest versions of Madwifi-NG and remove other VAPs
Source 0 (AtherosAG): Opening madwifi_ag source interface kis0...
Allowing clients to fetch WEP keys.
WARNING:  Disabling GPS logging.
Logging networks to /var/log/kismet/Kismet-Oct-22-2007-1.network
Logging networks in CSV format to /var/log/kismet/Kismet-Oct-22-2007-1.csv
Logging networks in XML format to /var/log/kismet/Kismet-Oct-22-2007-1.xml
Logging cryptographically weak packets to /var/log/kismet/Kismet-Oct-22-2007-1.weak
Logging cisco product information to /var/log/kismet/Kismet-Oct-22-2007-1.cisco
Logging data to /var/log/kismet/Kismet-Oct-22-2007-1.dump
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
Didn't detect any networks, unlinking network list.
Didn't detect any networks, unlinking CSV network list.
Didn't detect any networks, unlinking XML network list.
Didn't detect any Cisco Discovery Packets, unlinking cisco dump
wait: 86: No previous job
Kismet exited.
root@goooh:/etc/kismet# Didn't capture any packets, unlinking dump file
Didn't see any weak encryption packets, unlinking weak file
Kismet exiting.

```

Ifconfig/Iwconfig:

```

root@goooh:~# ifconfig
ath0      Link encap:Ethernet  HWaddr 00:40:96:A1:6E:A8  
          inet addr:198.123.51.233  Bcast:198.123.51.255  Mask:255.255.252.0
          inet6 addr: fe80::240:96ff:fea1:6ea8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4088 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2067085 (1.9 MB)  TX bytes:212611 (207.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26664 (26.0 KB)  TX bytes:26664 (26.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-40-96-A1-6E-A8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19902 errors:0 dropped:1784 overruns:0 frame:1411
          TX packets:1373 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:3561037 (3.3 MB)  TX bytes:246595 (240.8 KB)
          Interrupt:11 

root@goooh:~# iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:"ARC-WLAN-GUEST"  Nickname:""
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:0B:86:A1:69:A1   
          Bit Rate:48 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=47/70  Signal level=-47 dBm  Noise level=-94 dBm
          Rx invalid nwid:6207  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@goooh:~# 


```


When I try to sort the non-existent SSIDs, I get "Server is not reporting card power levels
.  No signal information available."

Any ideas?  Thanks!

---

### Post by rleechb on 2007-10-22
bump :guitar:

---

### Post by Siph0n on 2007-10-22
Did u try running kismet as root?

---

### Post by rleechb on 2007-10-22
yep, I can only run as root

---

### Post by Siph0n on 2007-10-23
I think kismet can only be run as root... There is documentation in the README about running it as non-root I believe... did you look there?

---

### Post by rleechb on 2007-10-23
My problem isn't running it as "non-root" ( think there's a .pid file listed that I can alter, if need be).  =D

The problem appears to be an issue with the madwifi drivers.  In monitor mode, I can't see any traffic, or send any traffic (busted out wireshark... don't see any 802.11 traffic @ all).

---

### Post by Siph0n on 2007-10-24
ok sorry, I can't help you lol.... Im not at that stage yet in my linux knowledge :)

---

### Post by rleechb on 2007-10-24
Thought I'd update.  Discovered that there's some sort of issue with the wpa supplicant interfering with monitor mode.  Anyways, a "killall wpa_supplicant" (during managed mode) fixed my issues.  :)

---

### Post by reidy90 on 2007-12-25
Yea I had a similar problem to you but couldn't get the above "killall wpa_supplicant" remedy to work.

I find if i disable ath0

*wlanconfig ath0 destroy*

and kismet starts fine.

but if i have it enabled, 
[I]
wlanconfig ath0 create wlandev wifi0 wlanmode managed[/I]

it produces the error in the first post. This did not used to happen, it has only started doing this since i started playing with aircrack-ng.

---

