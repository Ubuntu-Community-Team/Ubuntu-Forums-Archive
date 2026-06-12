---
title: "Need help with Kismet"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by digdug9117 on 2006-11-12
I have been trying to get Kismet running for a couple of hours help someone please help get this program running. I have an AR5212 NIC and using the madwifing_g for the source and wifi0 for interface.

Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (ATHEROS): Enabling monitor mode for madwifing_g source interface wifi0 channel 6...
NOTICE:  Created Madwifi-NG VAP kis
WARNING: wifi0 appears to be using Madwifi-NG.  Some versions of the Madwifi-NG drivers have problems in monitor mode, especially if non-monitor VAPs are active.  If you experience problems, be sure to try the latest versions of Madwifi-NG and remove other VAPs
Source 0 (ATHEROS): Opening madwifing_g source interface kis...
Allowing clients to fetch WEP keys.
WARNING:  Disabling GPS logging.
Logging networks to /var/log/kismet/Kismet-Nov-12-2006-1.network
Logging networks in CSV format to /var/log/kismet/Kismet-Nov-12-2006-1.csv
Logging networks in XML format to /var/log/kismet/Kismet-Nov-12-2006-1.xml
Logging cryptographically weak packets to /var/log/kismet/Kismet-Nov-12-2006-1.weak
Logging cisco product information to /var/log/kismet/Kismet-Nov-12-2006-1.cisco
Logging data to /var/log/kismet/Kismet-Nov-12-2006-1.dump
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
Kismet exiting.
[1] + Done                       ${BIN}/kismet_server --silent ${server}

when running iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"DaHood-wrt1"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:12:17:AC:83:9C   
          Bit Rate:48 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=33/94  Signal level=-62 dBm  Noise level=-95 dBm
          Rx invalid nwid:48390  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig

ath0      Link encap:Ethernet  HWaddr 00:14:6C:D5:29:33  
          inet addr:10.168.1.107  Bcast:10.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:6cff:fed5:2933/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4030 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4251289 (4.0 MiB)  TX bytes:636148 (621.2 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-14-6C-D5-29-33-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97883 errors:0 dropped:38 overruns:0 frame:64179
          TX packets:4367 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:14008131 (13.3 MiB)  TX bytes:813502 (794.4 KiB)
          Interrupt:10 Memory:d0c80000-d0c90000 


PLEASE HELP, Does anyone knows what I should do? ](*,)

---

### Post by spd106 on 2006-11-13
Did you follow the instructions on the madwifi site [http://madwifi.org/wiki/UserDocs/kismet](http://madwifi.org/wiki/UserDocs/kismet)?

Make sure you destroy any existing VAPs and comment out any settings for your interface in the /etc/network/interfaces file.

---

### Post by tturrisi on 2006-11-13
post your kismet.conf file, it should look like this:
```
 # User to setid to (should be your normal user)
suiduser=YOUR-UBUNTU-USERNAME

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=madwifi_ag,wifi0,madwifi
```

---

### Post by digdug9117 on 2006-11-13
Here is my kismet.conf

# User to setid to (should be your normal user)
suiduser=digdug

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=madwifi_g,wifi0,ATHEROS

---

### Post by digdug9117 on 2006-11-13
Now I'm not quite if madwifi is the right source because none of the madwifi commands are working for me like wlanconfig. Can someone please tell me how to find the right source drive to use.

---

### Post by hagan on 2006-12-02
Hello,
I have a similar problem, although I get a little further and the Kismet UI does start up. But I do not capture any packets. 
Googling around I find often the statment "to remove all existing VAPs". What is meant by this? How do I do that? It seems the madwifi tools (wlanconfig) are not available in Edgy. 
I do not have any entries in /et/network/interfaces, I use the Networkmanager tool with its control nm-applet. I tried to kill these, but still I do not capture any packets in Kismet.

Regards
Hagan

---

### Post by hagan on 2006-12-03
Hello,
I solved my problem. It seems to be enough to disable Wireless in th nm-applet application. ath0 is still there but does not influence kismet, which sets up its own VAP, called kis. It is not possible to monitor and communicate at the same time, but that is what I expected. Now everything works fine with kismet. But still I would like to have the wlanconfig tool, since some other monitoring programs (e.g. Wlanscanner) are not capable of setting up the required VAPs on their own.

Regards
Hagan

---

### Post by spd106 on 2006-12-03
You have to build madwifi-ng from [http://www.madwifi.org](http://www.madwifi.org) to get the wlanconfig tool. Neither Dapper, nor Edgy have it and I don't think Ubuntu ever will.

AFAIK you can send/receive on one VAP while another VAP is in monitor mode. I've done it with aircrack-ng, not sure about with kismet though, since I haven't used it much.

---

### Post by hagan on 2006-12-03
Hello,
thanks for the information. Makes not much sense to me, to include the drivers and not the tools. But since I had the whole build environment installed anyway, compiling the tools was not a big act. Everything works fine now.

Thanks
Hagan

PS: If somebody is also interested and does not want to compile on his own, just PM me, I can send you my tarred /usr/local tree. I compiled it against the standard Ubuntu kernel (2.6.17-10-generic). (makes probably no difference for the tools anyway)

---

