---
title: "need wireless to get off windows and use ubuntu"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by s-bris on 2007-02-06
Hi,

I installed ubuntu the other week hoping to move all my computers and family and friends onto Ubuntu. It all has gone well except for Wireless.  As all the computers are hooked up via wireless I am really hoping someone can shed some light on my problem so I can once an for all get off windows.  (all the windows boxes use wireless WPA-TKIP to Linksys routers.).

I downlaoded and installed 6.10 Ubuntu. I have been online via my wired LAN connection and downlaod all the updates.

All the windows boxes I need to replace are Dell notebooks and desktops and a few servers.  The current model I am trying to get wireless to work on os a Dell Inspirion 6000 with centrino.

I have checked the ubuntu install on the Dell Inspirion and everything seems fine when I have a wired LAN connection -> internet / email etc.. is great and so fast!


I tried and tried to follow the article: HOWTO: ipw2200 + wpa  by Luca_Linux but have run into many many problems ...


When I try :
sudo tar xvzf ieee80211-1.0.3.tgz
cd ieee80211-1.0.3

this is successful.  I do this in my home directory folder.

I noticed that the remove-old from the downlaod/extract doesn't have any execute privileges on it. So I updated it and tried to run it via:

sudo sh remove-old

and it came back with an error:

[: 9: ==: unexpected operator
remove-old: 11: KERN:=/: not found
remove-old: 13: Syntax error: "(" unexpected

Likewise when I did the following in my local home directory:

cd ..
sudo tar xvzf ipw2200-1.0.6.tgz
cd ipw2200-1.0.6

it works until I try and do the following:
sudo sh remove-old

I then have difficulties just running the make files:

steve@steve-laptop:~/steves-store/ubuntu/drivers-firmware/ieee80211-1.0.3$ sudo make
.: 4: remove-old: not found
make: *** [check_old] Error 2


and

steve@steve-laptop:~/steves-store/ubuntu/drivers-firmware/ipw2200-1.0.6$ sudo make
-e 
 ERROR: ieee80211.h not found in '/lib/modules/2.6.17-10-generic/include'.

You need to install the ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net)
and point this build to the location where you installed those sources, eg.:

% make IEEE80211_INC=/usr/src/ieee80211/

will look for ieee80211.h in /usr/src/ieee80211/net/

make: *** [check_inc] Error 1


I made the /etc/wpa_supplicant.conf as it details int he article with the ap_scan=2  etc.. and put the generated psk in the correct file location.

like:
ctrl_interface=/var/run/wpa_supplicant

network={
       ssid="my hidden SSID name"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       psk=the long generated key goes here
}



Here are the results from the rest of my commands that I tried like iwconfig, ifconfig, iwlist etc..


**_COMMAND0:_**
iwconfig

**_RESPONSE0:_**

steve@steve-laptop:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

**_COMMAND1:_**

iwlist scanning

**_RESPONSE1:_**

steve@steve-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0C:41:C1:B8:30
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=97/100  Signal level=-27 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 128ms ago
          Cell 02 - Address: 00:17:9A:1F:80:A2
                    ESSID:"ORPHEUS"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=29/100  Signal level=-82 dBm  
                    Extra: Last beacon: 1728ms ago
          Cell 03 - Address: 00:13:5F:55:26:E1
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=25/100  Signal level=-84 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : 802.1X  
                    Extra: Last beacon: 1712ms ago
          Cell 04 - Address: 00:02:6F:40:77:34
                    ESSID:"Internet Hotspot Dockside"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:5
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=61/100  Signal level=-64 dBm  
                    Extra: Last beacon: 1528ms ago
          Cell 05 - Address: 00:13:5F:55:26:E0
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=23/100  Signal level=-85 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 7320ms ago

sit0      Interface doesn't support scanning.

**_COMMAND2:_**
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -dd

**_RESPONSE2:_**

Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=11):
     62 65 42 62 23 2a 68 6f 4d 33 33                  beBb#*hoM33     
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
PSK - hexdump(len=32): [REMOVED]
Line 10: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Priority group 0
   id=0 ssid='beBb#*hoM33'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
SIOCGIWRANGE: WE(compiled)=20 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:13:ce:2b:d6:56
wpa_driver_ipw_set_wpa: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
bind(PF_UNIX): Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/eth1' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

Failed to add interface eth1
State: DISCONNECTED -> DISCONNECTED
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_set_wpa: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_drop_unencrypted: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
No keys have been configured - skip key clearing
WEXT: Operstate: linkmode=0, operstate=6
Cancelling scan request

**_COMMAND3:_**

ifconfig

**_RESPONSE3:_**

steve@steve-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:EB:83:E7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:212 (212.0 b)  TX bytes:212 (212.0 b)

**_HERE IS WHAT IT LOOKS LIKE WHEN CONNECTED VIA THE WIRED LAN:_**

steve@steve-laptop:/var/run$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:EB:83:E7  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:feeb:83e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3431 errors:0 dropped:0 overruns:0 frame:0
          TX packets:451 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:483803 (472.4 KiB)  TX bytes:38762 (37.8 KiB)
          Interrupt:201 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3500 (3.4 KiB)  TX bytes:3500 (3.4 KiB)

steve@steve-laptop:/var/run$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=2.40 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.724 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.725 ms


THANKS SO MUCH FOR ANY HELP....Steve

---

### Post by gradedcheese on 2007-02-06
Hi.  I can't help with your specific problem, but on a general note, don't do this:

sudo sh remove-old

You should instead, when running a script in the current working directory with sudo, do:

```

sudo ./remove-old

```

(note the ./ in front).  If the script isn't executable, make it executable first:

chmod +x remove-old

I believe that, when you run 'sh' in the way that you did, any environment variables set in your current shell won't be available in the new instance (of sh) and this might be why $KERN is undefined.  As for the 80211ieee.h error, it looks like the error message gives you some hints on what to do.

Another thing I'd like to mention: Ubuntu 6.10 comes with 'dash' instead of 'bash' as your default shell.  Many scripts were written to (incorrectly) assume that their user is running bash, and therefore might fail in dash.  You can change back to bash like this:

```

sudo rm /usr/bin/sh
sudo ln -s /usr/bin/bash /usr/bin/sh
exit

```
(and now open a new terminal)

I recommend that you do this in case one of the scripts you're running depends on bash but starts with #!/bin/sh instead of #!/bin/bash

---

### Post by s-bris on 2007-02-06
Thanks so much ... that helped with the remove.

Now my next problem seems to be surrounding the makefiles.  The doco I am workign off from luca-linux as mentioned in myu first post says to :

cd ..
cd ieee80211-1.0.3
make
sudo make install

and

cd ..
cd ipw2200-1.0.6
make
sudo make install

but when I go into the directory to do the make I get no where.  There is no make only a makefile and when I type in just make or sudo ./make nothing happens.  When I run sudo make install then somethings seem to run with a whole lot of errors....

thanks

---

### Post by gradedcheese on 2007-02-06
'make' is a command (located at /usr/bin/make), and not a script in the current directory.  So to 'make' you just type 'make', similar to running 'cd' to change directory.  Do you have make?  Try:

```

which make

```

If that doesn't return /usr/bin/make (or something very similar), then you need to install some tools.  As I recall you at least need to do:

```

sudo apt-get install binutils make gcc

```

Roughly speaking, the way that make works is it inspects the Makefile, which tells it what to do.  From there it knows to run a compiler (gcc), linker, etc to build from source.

---

