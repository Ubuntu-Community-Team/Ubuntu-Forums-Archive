---
title: "Wireless issues"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by bl00dninja on 2008-09-02
Hello friends,

            Just installed ubuntu 2 days back and got everything working. Had one issue I wanted to discuss and find solution on it. I am sure there are many threads open out there on this issue but I was not able to find the exact solution.

So I am not able to get my wireless up and running if it has an encryption key. If the wireless is open (not encrypted) I am able to get to it. Also I am not able to do this with the gui, I had to open a terminal window and type a bunch of commands to acomplish this, here is what I did

===================================================================

dpilankar@VW12206L:~$ sudo ifconfig wlan0 down

dpilankar@VW12206L:~$ sudo dhclient -r wlan0

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:de:86:48:2a
Sending on   LPF/wlan0/00:18:de:86:48:2a
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 10.0.0.4 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

dpilankar@VW12206L:~$ sudo ifconfig wlan0 up
dpilankar@VW12206L:~$ sudo iwconfig wlan0 essid "XXXXXXX"
dpilankar@VW12206L:~$ sudo iwconfig wlan0 key XXXXXXXX
dpilankar@VW12206L:~$ sudo iwconfig wlan0 key open
dpilankar@VW12206L:~$ sudo iwconfig wlan0 mode Managed
dpilankar@VW12206L:~$ sudo dhclient wlan0

There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:de:86:48:2a
Sending on   LPF/wlan0/00:18:de:86:48:2a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

dpilankar@VW12206L:~$ 

===================================================================
I am able to scan the wireless networks but somehow not able to connect it.

My wireless card info

  *-network               
       description: Wireless interface
       product: [COLOR="Blue"]**PRO/Wireless 3945ABG Network Connection**[/COLOR]
       vendor: [COLOR="Blue"]**Intel Corporation**[/COLOR]
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:86:48:2a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE


Please advice

Thanks

---

### Post by raul on 2008-09-04
I have exactly the same problem: same card, exactly the same command-line inputs give me exactly the same outputs. In my case, however, this only happens with my wireless connection at home--I can connect at coffee shops, school, etc. with no issues at all. I'm certain that the problem has nothing to do with the modem or the router: my wife's mac connects just fine. Also, I'm positive it has nothing to with WEP encryption: I've tried with no encryption, and with both 64 and 128 encryptions. 

I was wondering whether it might have to do with linux driver for the intel 3945 card. People with similar issues ([http://ubuntuforums.org/showthread.php?t=571188&highlight=dhcp\offers+received&page=18](http://ubuntuforums.org/showthread.php?t=571188&highlight=dhcp\offers+received&page=18)) were recommended to use the winXP divers, together with the latest version of ndiswrapper (1.53). They didn't report back whether that worked, though.

Anyone any thoughts?

---

### Post by Crafty Kisses on 2008-09-05
Post the results of this command: ```
lshw -C network
```

---

### Post by bl00dninja on 2008-09-06
thanks codename, its working now, took 2 days downloaded a bunch of updates and other softwares and somehow something fixed it, i wish i knew what it was. thanks for the help though.

---

