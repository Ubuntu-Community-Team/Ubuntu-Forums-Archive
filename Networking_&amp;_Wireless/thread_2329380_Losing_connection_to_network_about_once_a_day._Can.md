---
title: "Losing connection to network about once a day. Can't figure out why. [Ubuntu 16.04]"
date: 2016-06-30
forum: Networking &amp; Wireless
---

### Post by leetwanker on 2016-06-30
If someone could help me troubleshoot this, I'd appreciate it! 


The latest in a long series of disconnections happened @ 03:00. I've set up a little bash script on my laptop that notifies me when that computer goes offline. I unplugged and re-plugged the network cable @ 03:02.
   
Here's a tail of my /var/log/syslog going back about 35 minutes. 

    ```
    Jun 28 02:30:01 nvidia CRON[6966]: (justin) CMD (~/flexget/bin/flexget --cron --logfile ~/.flexget/flexgetcron.log execute)
    Jun 28 02:33:57 nvidia mono[984]: [Info] RssSyncService: Starting RSS Sync
    Jun 28 02:33:57 nvidia mono[984]: [Warn] FetchAndParseRssService: No available indexers. check your configuration.
    Jun 28 02:33:57 nvidia mono[984]: [Info] DownloadDecisionMaker: No results found
    Jun 28 02:33:57 nvidia mono[984]: [Info] RssSyncService: RSS Sync Completed. Reports found: 0, Reports grabbed: 0
    Jun 28 02:48:59 nvidia mono[984]: [Info] RssSyncService: Starting RSS Sync
    Jun 28 02:48:59 nvidia mono[984]: [Warn] FetchAndParseRssService: No available indexers. check your configuration.
    Jun 28 02:48:59 nvidia mono[984]: [Info] DownloadDecisionMaker: No results found
    Jun 28 02:48:59 nvidia mono[984]: [Info] RssSyncService: RSS Sync Completed. Reports found: 0, Reports grabbed: 0
    Jun 28 03:00:01 nvidia CRON[7371]: (justin) CMD (~/flexget/bin/flexget --cron --logfile ~/.flexget/flexgetcron.log execute)
    Jun 28 03:00:44 nvidia avahi-daemon[829]: Withdrawing address record for 192.168.1.100 on enp6s0.
    Jun 28 03:00:44 nvidia avahi-daemon[829]: Leaving mDNS multicast group on interface enp6s0.IPv4 with address 192.168.1.100.
    Jun 28 03:00:44 nvidia avahi-daemon[829]: Interface enp6s0.IPv4 no longer relevant for mDNS.
    Jun 28 03:00:45 nvidia whoopsie[849]: [03:00:45] Cannot reach: [https://daisy.ubuntu.com](https://daisy.ubuntu.com)
    Jun 28 03:00:45 nvidia whoopsie[849]: [03:00:45] offline
    Jun 28 03:00:45 nvidia ntpd[1417]: Deleting interface #8 enp6s0, 192.168.1.100#123, interface stats: received=584, sent=630, dropped=0, active_time=126089 secs
    Jun 28 03:00:45 nvidia ntpd[1417]: 198.60.73.8 local addr 192.168.1.100 -> <null>
    Jun 28 03:00:45 nvidia ntpd[1417]: 45.127.112.2 local addr 192.168.1.100 -> <null>
    Jun 28 03:00:45 nvidia ntpd[1417]: 138.236.128.36 local addr 192.168.1.100 -> <null>
    Jun 28 03:00:45 nvidia ntpd[1417]: 67.18.187.111 local addr 192.168.1.100 -> <null>
    Jun 28 03:00:45 nvidia ntpd[1417]: 199.102.46.78 local addr 192.168.1.100 -> <null>
    Jun 28 03:02:42 nvidia kernel: [300395.670917] sky2 0000:06:00.0 enp6s0: Link is down
    Jun 28 03:02:42 nvidia NetworkManager[857]: <info>  [1467097362.9311] device (enp6s0): link disconnected (deferring action for 4 seconds)
    Jun 28 03:02:44 nvidia ntpd[1417]: Deleting interface #9 enp6s0, fe80::42ea:6b0:7a07:d7ed%2#123, interface stats: received=0, sent=0, dropped=0, active_time=126208 secs
    Jun 28 03:02:46 nvidia NetworkManager[857]: <info>  [1467097366.3298] device (enp6s0): link connected
    Jun 28 03:02:46 nvidia kernel: [300399.244130] sky2 0000:06:00.0 enp6s0: Link is up at 1000 Mbps, full duplex, flow control both
    Jun 28 03:02:46 nvidia NetworkManager[857]: <info>  [1467097366.4422] device (enp6s0): DHCPv4 lease renewal requested
    Jun 28 03:02:46 nvidia NetworkManager[857]: <info>  [1467097366.5011] dhcp4 (enp6s0): canceled DHCP transaction, DHCP client pid 10699
    Jun 28 03:02:46 nvidia NetworkManager[857]: <info>  [1467097366.5011] dhcp4 (enp6s0): state changed bound -> done
    Jun 28 03:02:46 nvidia NetworkManager[857]: <info>  [1467097366.6027] dhcp4 (enp6s0): activation: beginning transaction (timeout in 45 seconds)
    Jun 28 03:02:46 nvidia NetworkManager[857]: <info>  [1467097366.8977] dhcp4 (enp6s0): dhclient started with pid 7411
    Jun 28 03:02:47 nvidia dhclient[7411]: DHCPREQUEST of 192.168.1.100 on enp6s0 to 255.255.255.255 port 67 (xid=0x6873b2c3)
    Jun 28 03:02:47 nvidia dhclient[7411]: DHCPACK of 192.168.1.100 from 192.168.1.1
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2069]   address 192.168.1.100
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2069]   plen 24 (255.255.255.0)
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2070]   gateway 192.168.1.1
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2070]   server identifier 192.168.1.1
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2070]   lease time 86400
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2070]   hostname 'nvidia'
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2070]   nameserver '192.168.1.1'
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2070]   domain name 'RT-N16'
    Jun 28 03:02:47 nvidia avahi-daemon[829]: Joining mDNS multicast group on interface enp6s0.IPv4 with address 192.168.1.100.
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2071]   wins '192.168.1.1'
    Jun 28 03:02:47 nvidia whoopsie[849]: [03:02:47] online
    Jun 28 03:02:47 nvidia avahi-daemon[829]: New relevant interface enp6s0.IPv4 for mDNS.
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2071] dhcp4 (enp6s0): state changed unknown -> bound
    Jun 28 03:02:47 nvidia avahi-daemon[829]: Registering new address record for 192.168.1.100 on enp6s0.IPv4.
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.3457] policy: set 'Wired connection 2' (enp6s0) as default for IPv4 routing and DNS
    Jun 28 03:02:47 nvidia dhclient[7411]: bound to 192.168.1.100 -- renewal in 38858 seconds.
    Jun 28 03:02:47 nvidia dbus[796]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
    Jun 28 03:02:47 nvidia systemd[1]: Starting Network Manager Script Dispatcher Service...
    Jun 28 03:02:48 nvidia dbus[796]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
    Jun 28 03:02:48 nvidia systemd[1]: Started Network Manager Script Dispatcher Service.
    Jun 28 03:02:48 nvidia nm-dispatcher: req:1 'dhcp4-change' [enp6s0]: new request (2 scripts)
    Jun 28 03:02:48 nvidia nm-dispatcher: req:1 'dhcp4-change' [enp6s0]: start running ordered scripts...
    Jun 28 03:02:48 nvidia ntpd[1417]: Listen normally on 10 enp6s0 192.168.1.100:123
    Jun 28 03:02:48 nvidia ntpd[1417]: Listen normally on 11 enp6s0 [fe80::42ea:6b0:7a07:d7ed%2]:123
    Jun 28 03:02:48 nvidia ntpd[1417]: new interface(s) found: waking up resolver
    Jun 28 03:02:49 nvidia ntpd[1417]: Soliciting pool server 204.9.54.119
    Jun 28 03:02:50 nvidia ntpd[1417]: Soliciting pool server 69.50.219.51
    Jun 28 03:04:02 nvidia mono[984]: [Info] RssSyncService: Starting RSS Sync
    Jun 28 03:04:02 nvidia mono[984]: [Warn] FetchAndParseRssService: No available indexers. check your configuration.
    Jun 28 03:04:02 nvidia mono[984]: [Info] DownloadDecisionMaker: No results found
    Jun 28 03:04:02 nvidia mono[984]: [Info] RssSyncService: RSS Sync Completed. Reports found: 0, Reports grabbed: 0
    Jun 28 03:05:24 nvidia systemd[1]: Started Session 271 of user justin.
```

I've been able to get it to reconnect to the network by running `sudo dhclient`, but as I don't keep a keyboard plugged into the system, it's easier just to bring it back up physically. 

I've replaced the network cable with a new one, no luck there.

Found in /var/log/kern.log

    ```
    Jun 28 03:02:42 nvidia kernel: [300395.670917] sky2 0000:06:00.0 enp6s0: Link is down
    Jun 28 03:02:42 nvidia NetworkManager[857]: <info>  [1467097362.9311] device (enp6s0): link disconnected (deferring action for 4 seconds)
    Jun 28 03:02:46 nvidia NetworkManager[857]: <info>  [1467097366.3298] device (enp6s0): link connected
    Jun 28 03:02:46 nvidia kernel: [300399.244130] sky2 0000:06:00.0 enp6s0: Link is up at 1000 Mbps, full duplex, flow control both
    Jun 28 03:02:46 nvidia NetworkManager[857]: <info>  [1467097366.4422] device (enp6s0): DHCPv4 lease renewal requested
    Jun 28 03:02:46 nvidia NetworkManager[857]: <info>  [1467097366.5011] dhcp4 (enp6s0): canceled DHCP transaction, DHCP client pid 10699
    Jun 28 03:02:46 nvidia NetworkManager[857]: <info>  [1467097366.5011] dhcp4 (enp6s0): state changed bound -> done
    Jun 28 03:02:46 nvidia NetworkManager[857]: <info>  [1467097366.6027] dhcp4 (enp6s0): activation: beginning transaction (timeout in 45 seconds)
    Jun 28 03:02:46 nvidia NetworkManager[857]: <info>  [1467097366.8977] dhcp4 (enp6s0): dhclient started with pid 7411
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2069]   address 192.168.1.100
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2069]   plen 24 (255.255.255.0)
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2070]   gateway 192.168.1.1
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2070]   server identifier 192.168.1.1
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2070]   lease time 86400
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2070]   hostname 'nvidia'
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2070]   nameserver '192.168.1.1'
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2070]   domain name 'RT-N16'
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2071]   wins '192.168.1.1'
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.2071] dhcp4 (enp6s0): state changed unknown -> bound
    Jun 28 03:02:47 nvidia NetworkManager[857]: <info>  [1467097367.3457] policy: set 'Wired connection 2' (enp6s0) as default for IPv4 routing and DNS
```

---

