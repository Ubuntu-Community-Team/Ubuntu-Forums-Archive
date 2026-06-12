---
title: "Issue with reboot, it takes ages with wlan enabled"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by giruzz on 2006-11-24
Hi,

I've been able to use my wifi connection with WPA using the script that you can find [here]("http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa")

If I'm following the suggestion posted [here]("http://ubuntuforums.org/showpost.php?p=1351902&postcount=2") the system works and takes ages,

```

cd /etc/init.d/
sudo gedit wireless-network.sh

```

```

/etc/init.d/networking restart

```


```

sudo chmod +x wireless-network.sh

```

```

sudo ln -s /etc/init.d/wireless-network.sh S40wireless-network

```



if I'm using [these]("http://ubuntuforums.org/showpost.php?p=1796725&postcount=50") scripts the wifi connection doesn't work at all

```
echo 'ifdown wlan0' >/etc/init.d/WlanDown
ln -s ../init.d/WlanDown /etc/rcS.d/S40WlanDown
```

then


```
chmod +x /etc/init.d/WlanDown
```

or

```
sudo bash -c 'echo "ifdown wlan0" >/etc/init.d/WlanDown'
```
and then
```
chmod +x /etc/init.d/WlanDown
```

it doesn't work at all...

any suggestion?

thanks

g.

---

### Post by wieman01 on 2006-11-24
I think I know what your problem is concerning the first script... When the network is brought up the system clock tries to synchronize with a server on the Internet. For some reason, this creates a problem when restarting the network during boot. I had a similar issue a while ago, and the solution was to disable the sync-function.

I'll post a solution later tonight... need to find the relevant line first (in "/etc/init.d/networking"?) that you need to comment '#'. Once you do that, you won't have a timeout issue anymore.

---

### Post by tedrogers on 2006-11-24
I just tried enabling my time-sync and it made no difference to my boot time.

Not that this might not still be the problem @giruzz.

@Wieman: Could it be something to do with the boot sequence? This page [http://www.linux.com/article.pl?sid=04/06/23/1734235]("http://www.linux.com/article.pl?sid=04/06/23/1734235") suggests that the boot sequence should be S45, as highlighted below:

```
S10sysklogd       S20ppp          S99gpm
S12kerneld        S25netstd_nfs   S99httpd
S15netstd_init    S30netstd_misc  S99rmnologin
S18netbase        **S45pcmcia**       S99sshd
S20acct           S89atd
S20logoutd        S89cron
```

Does this help at all?

---

### Post by wieman01 on 2006-11-24
It could be the boot sequence... But I thought that S40 is actually the right range reserved for networking. I'll check that back home once again & also see where we can find the "sync" function. Perhaps you find something in the meantime. The discussion is definitely going in the right direction.

The symb-links to basic services such as networking should be placed here:
> cd /etc/rcS.d/
_**EDIT:**_
Plus this works for a number of other users... Let me check back home.

---

### Post by wieman01 on 2006-11-24
Giruzz:

Run this command from command line:
> sudo gedit /etc/network/if-up.d/ntpdate
Then comment all lines ("put a hash in from of every line - this stops it from working") so that it looks like this:
> #!/bin/sh
# Adjust the system clock with ntp whenever a network interface is
# brought up, as it might mean we can contact the server.

#[ "$IFACE" != "lo" ] || exit 0
#
#test -f /usr/sbin/ntpdate || exit 0
#
#if [ -f /etc/default/ntpdate ]; then
#	. /etc/default/ntpdate
#	test -n "$NTPSERVERS" || exit 0
#else
#	NTPSERVERS="ntp.ubuntu.com"
#fi
#
#if [ "$VERBOSITY" = 1 ]; then
#	echo "Synchronizing clock to $NTPSERVERS..."
#	/usr/sbin/ntpdate -b -s $NTPOPTIONS $NTPSERVERS || true
#else
#	/usr/sbin/ntpdate -b -s $NTPOPTIONS $NTPSERVERS >/dev/null 2>&1 || true
#fi
Save the file & reboot the computer. Still the same problem?

---

### Post by giruzz on 2006-11-24
> **wieman01 said:**
> Giruzz:

Run this command from command line:

Then comment all lines ("put a hash in from of every line - this stops it from working") so that it looks like this:

Save the file & reboot the computer. Still the same problem?

The problem is still here :(

just two little things:

1) I have to use 'sudo /etc/init.d/networking restart' or the script doesn't work

2) If I use S40 the script doesn't work. I used S43

bye

g.

---

### Post by wieman01 on 2006-11-25
Also the same problem when you use S43? What exactly happens during boot? Can you check the boot log-file and post the contents here?
> cd /var/log/
In this folder there should be a file called "boot.log" or similar. I have disabled the log function, therefore I cannot tell for sure what name it has. Open it with "gedit" and paste the contents in here.

---

### Post by giruzz on 2006-11-25
Here we go:

```
Nov 25 14:05:44 rcS:  * Reading files needed to boot...       [80G 
[74G[ ok ]
Nov 25 14:05:45 rcS:  * Setting preliminary keymap...       [80G 
[74G[ ok ]
Nov 25 14:05:45 rcS:  * Preparing restricted drivers...       [80G 
[74G[ ok ]
Nov 25 14:05:45 rcS:  * Starting basic networking...       [80G 
[74G[ ok ]
Nov 25 14:05:45 rcS:  * Starting kernel event manager...       [80G 
[74G[ ok ]
Nov 25 14:05:46 rcS:  * Loading hardware drivers...       [80G 
[74G[ ok ]
Nov 25 14:05:46 rcS:  * Loading manual drivers...       [80G 
[74G[ ok ]
Nov 25 14:05:46 rcS:  * Mounting local filesystems...       [80G 
[74G[ ok ]
Nov 25 14:05:46 rcS:  * Activating swapfile swap...       [80G 
[74G[ ok ]
Nov 25 14:05:47 rcS:  * Reconfiguring network interfaces...       [80G There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Nov 25 14:05:47 rcS: Internet Systems Consortium DHCP Client V3.0.4
Nov 25 14:05:47 rcS: Copyright 2004-2006 Internet Systems Consortium.
Nov 25 14:05:47 rcS: All rights reserved.
Nov 25 14:05:47 rcS: For info, please visit http://www.isc.org/sw/dhcp/
Nov 25 14:05:47 rcS: 
Nov 25 14:05:47 rcS: Listening on LPF/eth0/00:c0:9f:95:d4:92
Nov 25 14:05:47 rcS: Sending on   LPF/eth0/00:c0:9f:95:d4:92
Nov 25 14:05:47 rcS: Sending on   Socket/fallback
Nov 25 14:05:47 rcS: DHCPRELEASE on eth0 to 192.168.0.1 port 67
Nov 25 14:05:47 rcS: send_packet: Network is unreachable
Nov 25 14:05:47 rcS: send_packet: please consult README file regarding broadcast address.
Nov 25 14:05:47 rcS: There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Nov 25 14:05:47 rcS: Internet Systems Consortium DHCP Client V3.0.4
Nov 25 14:05:47 rcS: Copyright 2004-2006 Internet Systems Consortium.
Nov 25 14:05:47 rcS: All rights reserved.
Nov 25 14:05:47 rcS: For info, please visit http://www.isc.org/sw/dhcp/
Nov 25 14:05:47 rcS: 
Nov 25 14:05:47 rcS: Listening on LPF/eth1/00:12:f0:64:69:63
Nov 25 14:05:47 rcS: Sending on   LPF/eth1/00:12:f0:64:69:63
Nov 25 14:05:47 rcS: Sending on   Socket/fallback
Nov 25 14:05:47 rcS: DHCPRELEASE on eth1 to 192.168.0.1 port 67
Nov 25 14:05:47 rcS: send_packet: Network is unreachable
Nov 25 14:05:47 rcS: send_packet: please consult README file regarding broadcast address.
Nov 25 14:05:47 rcS: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Nov 25 14:05:47 rcS: Internet Systems Consortium DHCP Client V3.0.4
Nov 25 14:05:47 rcS: Copyright 2004-2006 Internet Systems Consortium.
Nov 25 14:05:47 rcS: All rights reserved.
Nov 25 14:05:47 rcS: For info, please visit http://www.isc.org/sw/dhcp/
Nov 25 14:05:47 rcS: 
Nov 25 14:05:48 rcS: Listening on LPF/eth0/00:c0:9f:95:d4:92
Nov 25 14:05:48 rcS: Sending on   LPF/eth0/00:c0:9f:95:d4:92
Nov 25 14:05:48 rcS: Sending on   Socket/fallback
Nov 25 14:05:48 rcS: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Nov 25 14:05:54 rcS: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 25 14:06:01 rcS: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov 25 14:06:12 rcS: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Nov 25 14:06:33 rcS: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Nov 25 14:06:49 rcS: No DHCPOFFERS received.
Nov 25 14:06:49 rcS: No working leases in persistent database - sleeping.
Nov 25 14:06:49 rcS: There is already a pid file /var/run/dhclient.eth1.pid with pid 3377
Nov 25 14:06:49 rcS: killed old client process, removed PID file
Nov 25 14:06:49 rcS: Internet Systems Consortium DHCP Client V3.0.4
Nov 25 14:06:49 rcS: Copyright 2004-2006 Internet Systems Consortium.
Nov 25 14:06:49 rcS: All rights reserved.
Nov 25 14:06:49 rcS: For info, please visit http://www.isc.org/sw/dhcp/
Nov 25 14:06:49 rcS: 
Nov 25 14:06:50 rcS: Listening on LPF/eth1/00:12:f0:64:69:63
Nov 25 14:06:50 rcS: Sending on   LPF/eth1/00:12:f0:64:69:63
Nov 25 14:06:50 rcS: Sending on   Socket/fallback
Nov 25 14:06:50 rcS: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Nov 25 14:06:52 rcS: DHCPOFFER from 192.168.0.1
Nov 25 14:06:52 rcS: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Nov 25 14:06:52 rcS: DHCPACK from 192.168.0.1
Nov 25 14:06:52 rcS: bound to 192.168.0.4 -- renewal in 39073 seconds.
Nov 25 14:06:52 rcS: Internet Systems Consortium DHCP Client V3.0.4
Nov 25 14:06:52 rcS: Copyright 2004-2006 Internet Systems Consortium.
Nov 25 14:06:52 rcS: All rights reserved.
Nov 25 14:06:52 rcS: For info, please visit http://www.isc.org/sw/dhcp/
Nov 25 14:06:52 rcS: 
Nov 25 14:06:52 rcS: SIOCSIFADDR: No such device
Nov 25 14:06:52 rcS: eth2: ERROR while getting interface flags: No such device
Nov 25 14:06:52 rcS: eth2: ERROR while getting interface flags: No such device
Nov 25 14:06:53 rcS: Bind socket to interface: No such device
Nov 25 14:06:53 rcS: Failed to bring up eth2.
Nov 25 14:06:53 rcS: Internet Systems Consortium DHCP Client V3.0.4
Nov 25 14:06:53 rcS: Copyright 2004-2006 Internet Systems Consortium.
Nov 25 14:06:53 rcS: All rights reserved.
Nov 25 14:06:53 rcS: For info, please visit http://www.isc.org/sw/dhcp/
Nov 25 14:06:53 rcS: 
Nov 25 14:06:53 rcS: SIOCSIFADDR: No such device
Nov 25 14:06:53 rcS: ath0: ERROR while getting interface flags: No such device
Nov 25 14:06:53 rcS: ath0: ERROR while getting interface flags: No such device
Nov 25 14:06:54 rcS: Bind socket to interface: No such device
Nov 25 14:06:54 rcS: Failed to bring up ath0.
Nov 25 14:06:54 rcS: Internet Systems Consortium DHCP Client V3.0.4
Nov 25 14:06:54 rcS: Copyright 2004-2006 Internet Systems Consortium.
Nov 25 14:06:54 rcS: All rights reserved.
Nov 25 14:06:54 rcS: For info, please visit http://www.isc.org/sw/dhcp/
Nov 25 14:06:54 rcS: 
Nov 25 14:06:54 rcS: SIOCSIFADDR: No such device
Nov 25 14:06:54 rcS: wlan0: ERROR while getting interface flags: No such device
Nov 25 14:06:54 rcS: wlan0: ERROR while getting interface flags: No such device
Nov 25 14:06:55 rcS: Bind socket to interface: No such device
Nov 25 14:06:55 rcS: Failed to bring up wlan0.
Nov 25 14:06:55 rcS: 
[74G[ ok ]
Nov 25 14:06:59 rcS:  * Configuring network interfaces...       [80G 
[74G[ ok ]
Nov 25 14:06:59 rcS:  * Reconfiguring network interfaces...       [80G There is already a pid file /var/run/dhclient.eth0.pid with pid 3385
Nov 25 14:06:59 rcS: killed old client process, removed PID file
Nov 25 14:06:59 rcS: Internet Systems Consortium DHCP Client V3.0.4
Nov 25 14:06:59 rcS: Copyright 2004-2006 Internet Systems Consortium.
Nov 25 14:06:59 rcS: All rights reserved.
Nov 25 14:06:59 rcS: For info, please visit http://www.isc.org/sw/dhcp/
Nov 25 14:06:59 rcS: 
Nov 25 14:06:59 rcS: Listening on LPF/eth0/00:c0:9f:95:d4:92
Nov 25 14:06:59 rcS: Sending on   LPF/eth0/00:c0:9f:95:d4:92
Nov 25 14:06:59 rcS: Sending on   Socket/fallback
Nov 25 14:06:59 rcS: DHCPRELEASE on eth0 to 192.168.0.1 port 67
Nov 25 14:06:59 rcS: There is already a pid file /var/run/dhclient.eth1.pid with pid 3445
Nov 25 14:06:59 rcS: killed old client process, removed PID file
Nov 25 14:06:59 rcS: Internet Systems Consortium DHCP Client V3.0.4
Nov 25 14:06:59 rcS: Copyright 2004-2006 Internet Systems Consortium.
Nov 25 14:06:59 rcS: All rights reserved.
Nov 25 14:06:59 rcS: For info, please visit http://www.isc.org/sw/dhcp/
Nov 25 14:06:59 rcS: 
Nov 25 14:06:59 rcS: Listening on LPF/eth1/00:12:f0:64:69:63
Nov 25 14:06:59 rcS: Sending on   LPF/eth1/00:12:f0:64:69:63
Nov 25 14:06:59 rcS: Sending on   Socket/fallback
Nov 25 14:06:59 rcS: DHCPRELEASE on eth1 to 192.168.0.1 port 67
Nov 25 14:06:59 rcS: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Nov 25 14:06:59 rcS: Internet Systems Consortium DHCP Client V3.0.4
Nov 25 14:06:59 rcS: Copyright 2004-2006 Internet Systems Consortium.
Nov 25 14:06:59 rcS: All rights reserved.
Nov 25 14:06:59 rcS: For info, please visit http://www.isc.org/sw/dhcp/
Nov 25 14:06:59 rcS: 
Nov 25 14:07:00 rcS: Listening on LPF/eth0/00:c0:9f:95:d4:92
Nov 25 14:07:00 rcS: Sending on   LPF/eth0/00:c0:9f:95:d4:92
Nov 25 14:07:00 rcS: Sending on   Socket/fallback
Nov 25 14:07:02 rcS: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov 25 14:07:07 rcS: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 25 14:07:14 rcS: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Nov 25 14:07:27 rcS: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Nov 25 14:07:46 rcS: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Nov 25 14:07:56 rcS: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Nov 25 14:08:03 rcS: No DHCPOFFERS received.
Nov 25 14:08:03 rcS: No working leases in persistent database - sleeping.
Nov 25 14:08:03 rcS: There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Nov 25 14:08:03 rcS: Internet Systems Consortium DHCP Client V3.0.4
Nov 25 14:08:03 rcS: Copyright 2004-2006 Internet Systems Consortium.
Nov 25 14:08:03 rcS: All rights reserved.
Nov 25 14:08:03 rcS: For info, please visit http://www.isc.org/sw/dhcp/
Nov 25 14:08:03 rcS: 
Nov 25 14:08:04 rcS: Listening on LPF/eth1/00:12:f0:64:69:63
Nov 25 14:08:04 rcS: Sending on   LPF/eth1/00:12:f0:64:69:63
Nov 25 14:08:04 rcS: Sending on   Socket/fallback
Nov 25 14:08:06 rcS: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Nov 25 14:08:06 rcS: DHCPOFFER from 192.168.0.1
Nov 25 14:08:06 rcS: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Nov 25 14:08:06 rcS: DHCPACK from 192.168.0.1
Nov 25 14:08:06 rcS: bound to 192.168.0.4 -- renewal in 35307 seconds.
Nov 25 14:08:06 rcS: There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Nov 25 14:08:06 rcS: Internet Systems Consortium DHCP Client V3.0.4
Nov 25 14:08:06 rcS: Copyright 2004-2006 Internet Systems Consortium.
Nov 25 14:08:06 rcS: All rights reserved.
Nov 25 14:08:06 rcS: For info, please visit http://www.isc.org/sw/dhcp/
Nov 25 14:08:06 rcS: 
Nov 25 14:08:06 rcS: SIOCSIFADDR: No such device
Nov 25 14:08:06 rcS: eth2: ERROR while getting interface flags: No such device
Nov 25 14:08:06 rcS: eth2: ERROR while getting interface flags: No such device
Nov 25 14:08:07 rcS: Bind socket to interface: No such device
Nov 25 14:08:07 rcS: Failed to bring up eth2.
Nov 25 14:08:07 rcS: There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Nov 25 14:08:07 rcS: Internet Systems Consortium DHCP Client V3.0.4
Nov 25 14:08:07 rcS: Copyright 2004-2006 Internet Systems Consortium.
Nov 25 14:08:07 rcS: All rights reserved.
Nov 25 14:08:07 rcS: For info, please visit http://www.isc.org/sw/dhcp/
Nov 25 14:08:07 rcS: 
Nov 25 14:08:07 rcS: SIOCSIFADDR: No such device
Nov 25 14:08:07 rcS: ath0: ERROR while getting interface flags: No such device
Nov 25 14:08:07 rcS: ath0: ERROR while getting interface flags: No such device
Nov 25 14:08:08 rcS: Bind socket to interface: No such device
Nov 25 14:08:08 rcS: Failed to bring up ath0.
Nov 25 14:08:08 rcS: There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Nov 25 14:08:08 rcS: Internet Systems Consortium DHCP Client V3.0.4
Nov 25 14:08:08 rcS: Copyright 2004-2006 Internet Systems Consortium.
Nov 25 14:08:08 rcS: All rights reserved.
Nov 25 14:08:08 rcS: For info, please visit http://www.isc.org/sw/dhcp/
Nov 25 14:08:08 rcS: 
Nov 25 14:08:08 rcS: SIOCSIFADDR: No such device
Nov 25 14:08:08 rcS: wlan0: ERROR while getting interface flags: No such device
Nov 25 14:08:08 rcS: wlan0: ERROR while getting interface flags: No such device
Nov 25 14:08:09 rcS: Bind socket to interface: No such device
Nov 25 14:08:09 rcS: Failed to bring up wlan0.
Nov 25 14:08:09 rcS: 
[74G[ ok ]
Nov 25 14:08:09 rcS:  * Setting up console font and keymap...       [80G 
[74G[ ok ]
Nov 25 14:08:10 rc2:  * Saving VESA state...       [80G 
[74G[ ok ]
Nov 25 14:08:11 rc2:  * Loading ACPI modules...       [80G 
[74G[ ok ]
Nov 25 14:08:11 rc2:  * Starting ACPI services...       [80G 
[74G[ ok ]
Nov 25 14:08:11 rc2:  * Starting system log...       [80G 
[74G[ ok ]
Nov 25 14:08:11 rc2:  * Starting kernel log...       [80G 
[74G[ ok ]
Nov 25 14:08:11 rc2: Starting K Display Manager: kdm.
Nov 25 14:08:12 rc2:  * Starting Common Unix Printing System: cupsd       [80G 
[74G[ ok ]
Nov 25 14:08:14 rc2:  * Starting HP Linux Printing and Imaging System       [80G 
[74G[ ok ]
Nov 25 14:08:14 rc2:  * Starting apt index watcher apt-index-watcher       [80G 
[74G[ ok ]
Nov 25 14:08:14 rc2:  * Starting system message bus dbus       [80G 
[74G[ ok ]
Nov 25 14:08:17 rc2:  * Starting Hardware abstraction layer hald       [80G 
[74G[ ok ]
Nov 25 14:08:17 rc2:  * Starting powernowd...        [80G 
[74G[ ok ]
Nov 25 14:08:18 rc2:  * Starting Bluetooth services       [80G 
[74G[ ok ]
Nov 25 14:08:18 rc2:  * Starting anac(h)ronistic cron: anacron       [80G 
[74G[ ok ]
Nov 25 14:08:18 rc2:  * Starting deferred execution scheduler atd       [80G 
[74G[ ok ]
Nov 25 14:08:18 rc2:  * Starting periodic command scheduler...       [80G 
[74G[ ok ]
Nov 25 14:08:18 rc2:  * Checking battery state...       [80G 
[74G[ ok ]
Nov 25 14:08:18 rc2:  * Running local boot scripts (/etc/rc.local)       [80G 
[74G[ ok ]

```

---

### Post by wieman01 on 2006-11-25
Can you please post the contents of this file...
> sudo gedit /etc/network/interfaces
Just remove your network-key and anything else that you consider confidential. I think I may know what your problem is.

---

### Post by giruzz on 2006-11-25
Thanks for you help! I really appreciate you efforts ...

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid The_house_of_love
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk REMOVED
auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

---

### Post by wieman01 on 2006-11-26
You're welcome. Now please update the file according to this & restart the PC:
> auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid The_house_of_love
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk REMOVED
Any better?

---

### Post by tedrogers on 2006-11-26
You just beat me to it Wieman....I was going to suggest removing eth0, eth2, ath0 and wlan0 from the interfaces file.

Hope this works now.

---

### Post by giruzz on 2006-11-26
Hi,

It works! My boot is much much faster (3 minutes faster than before!!)

wieman01 you should add this advice (disabling other network interface from reboot) in your how-to!

Thanks guys for your help! I really appreciated that!

(Now I'm a really happy newbie with Linux)!

giruzz

---

### Post by wieman01 on 2006-11-26
Great... I have not mentioned this so far, because this is rather networking related than wireless security. But I'll think about it & see if I put it in the appendix. Have fun with it!

---

### Post by tedrogers on 2006-11-26
So I suppose the problem was that Ubuntu was checking all of the interfaces listed...and waiting to time-out before booting.

By the way, the wireless set-up doesn't like having wired and wireless in the same config as I understand.

Anyway....glad that you're all up and running now. :)

---

### Post by FenderReplica on 2007-07-28
From learning to use ndiswrapper for my WG111v2 to getting WPA support working took me some time but I absolutely enjoyed it.

Kudos for Wiseman01 posting the simple method which over 10k people seek help from and most of us benefited from it.

I would like to know why it took me 2 reboots to get ifup correctly for wlan0 after using the echo method to add ifdown sequence before network reboot at S40. What could be the reason for this as I am curious.

Will let you know if WPA works after 3rd reboot tomorrow.

Onces again, thanks a lot you guys

---

### Post by wieman01 on 2007-07-29
> **FenderReplica said:**
> I would like to know why it took me 2 reboots to get ifup correctly for wlan0 after using the echo method to add ifdown sequence before network reboot at S40. What could be the reason for this as I am curious

Good question. All I can say is that I suspect this is a bug. I have a similar problem on my desktop PC which uses "ndiswrapper". I would disconnect occasionally and won't reconnect until I reboot the PC once or even twice. 

Let us know how you go.

---

### Post by FenderReplica on 2007-08-06
Wieman01

Hmm, I have been using WlanDown script described in ur post in order to sort out the situation where you need to manually ifdown and ifup after restart but it turned out to be unsucessful...

Boot up time is still long so i ls the content in rcS.d and found out that i have 2 S40 process, namely networking and WlanDown, WlanDown contains the function ifdown wlan0

I thought that having 2 S40 process would colide the network start up process so I tidied up the process to S39 for WlanDown and S40 for networking, I have "cat" S39 link to check it was propa linked

Now every time I restart it takes uber long to start up, process bar stuck at 1/3 for nearly 2 mins before moving on...

And desktop manager like beryl starts to be loading slow after log in as well....

Apart from the 2nd reboot I had mention before that yielded a sucessful start up, other reboots gave a doggy ouput in "ifconfig"

there's an interface alias wlan0:avah which registered itself with wrong brocast ip and wrong ip was assigned to this device....

I have to manually ifdown and ifup every time i reboot.... which is kinda annoying.

Now i have deleted S39WlanDown within rcS.d and considering using ur script in original post #2

But it's just a network restart script isn't it? when i did it after restart DHCPDISCOVER fail to obtain valid lease (i believe that's what it told me)

Could that be wext driver that's acting up? I suspect this becoz i used a wrong driver for my WG111v2 before and it had showed the device wlan0:avah when the driver wasn't right..(once i had gotten the driver rite for ndiswrapper wlan0:avah was gone)

Any thoughts?

Cheers

---

