---
title: "[SOLVED] Shorewall Config for Wireless Router (Help?)"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by sjokomunn on 2008-11-06
I am using the latest version of shorewall. I have been stumped for a while now and have decided to post here while I continue to research.

I am using an ubuntu box as a wireless router going directly into the cable modem. There is no wired LAN, just the net (eth0) and WLAN (ath0). Clients can connect to the access point fine but are unable to access the net. IP_FORWARDING=Yes (Is this the same as =Keep which was set by default?) I will post some errors from syslog and my shorewall configs below in hopes that someone can shed some light.

Syslogs:
```
Nov  6 19:09:03 ubuntu dibble: Shorewall restarted
Nov  6 19:09:45 ubuntu hostapd: ath0: STA 00:12:f0:8f:4c:24 IEEE 802.11: associated
Nov  6 19:09:45 ubuntu hostapd: ath0: STA 00:12:f0:8f:4c:24 WPA: pairwise key handshake completed (RSN)
Nov  6 19:09:45 ubuntu hostapd: ath0: STA 00:12:f0:8f:4c:24 WPA: group key handshake completed (RSN)
Nov  6 19:09:51 ubuntu dhcpd: DHCPDISCOVER from 00:12:f0:8f:4c:24 via ath0
Nov  6 19:09:51 ubuntu dhcpd: icmp_echorequest 192.168.0.203: Operation not permitted
Nov  6 19:09:51 ubuntu kernel: [80997.024959] Shorewall:OUTPUT:REJECT:IN= OUT=ath0 SRC=192.168.0.1 DST=192.168.0.203 LEN=48 TOS=0x00 PR$
Nov  6 19:09:52 ubuntu dhcpd: DHCPOFFER on 192.168.0.203 to 00:12:f0:8f:4c:24 (skankabilly) via ath0
Nov  6 19:09:52 ubuntu dhcpd: Wrote 2 leases to leases file.
Nov  6 19:09:52 ubuntu dhcpd: DHCPREQUEST for 192.168.0.203 (192.168.0.1) from 00:12:f0:8f:4c:24 (skankabilly) via ath0
Nov  6 19:09:52 ubuntu dhcpd: DHCPACK on 192.168.0.203 to 00:12:f0:8f:4c:24 (skankabilly) via ath0
Nov  6 19:09:52 ubuntu dhcpd: DHCPREQUEST for 192.168.0.203 (192.168.0.1) from 00:12:f0:8f:4c:24 (skankabilly) via ath0
Nov  6 19:09:52 ubuntu dhcpd: DHCPACK on 192.168.0.203 to 00:12:f0:8f:4c:24 (skankabilly) via ath0
Nov  6 19:11:04 ubuntu kernel: [81069.918663] Shorewall:INPUT:REJECT:IN=ath0 OUT= MAC=00:1d:6a:17:c4:2d:00:12:f0:8f:4c:24:08:00:45:00:0$
Nov  6 19:11:04 ubuntu dhcpd: DHCPRELEASE of 192.168.0.203 from 00:12:f0:8f:4c:24 (skankabilly) via ath0 (found)
Nov  6 19:11:05 ubuntu hostapd: ath0: STA 00:12:f0:8f:4c:24 IEEE 802.11: disassociated
Nov  6 19:17:01 ubuntu /USR/SBIN/CRON[9465]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  6 19:17:03 ubuntu kernel: [81429.176090] wifi0: ath_bstuck_tasklet: Stuck beacon; resetting (beacon miss count: 11)
Nov  6 19:17:03 ubuntu kernel: [81429.483044] wifi0: ath_bstuck_tasklet: Stuck beacon; resetting (beacon miss count: 11)
Nov  6 19:17:04 ubuntu dibble: Shorewall restarted
Nov  6 19:17:17 ubuntu hostapd: ath0: STA 00:12:f0:8f:4c:24 IEEE 802.11: associated
Nov  6 19:17:18 ubuntu hostapd: ath0: STA 00:12:f0:8f:4c:24 WPA: pairwise key handshake completed (RSN)
Nov  6 19:17:21 ubuntu dhcpd: DHCPDISCOVER from 00:12:f0:8f:4c:24 via ath0
Nov  6 19:17:21 ubuntu dhcpd: icmp_echorequest 192.168.0.203: Operation not permitted
Nov  6 19:17:21 ubuntu kernel: [81447.404671] Shorewall:OUTPUT:REJECT:IN= OUT=ath0 SRC=192.168.0.1 DST=192.168.0.203 LEN=48 TOS=0x00 PR$
Nov  6 19:17:22 ubuntu dhcpd: DHCPOFFER on 192.168.0.203 to 00:12:f0:8f:4c:24 (skankabilly) via ath0
Nov  6 19:17:22 ubuntu dhcpd: DHCPREQUEST for 192.168.0.203 (192.168.0.1) from 00:12:f0:8f:4c:24 (skankabilly) via ath0
Nov  6 19:17:22 ubuntu dhcpd: DHCPACK on 192.168.0.203 to 00:12:f0:8f:4c:24 (skankabilly) via ath0
Nov  6 19:17:22 ubuntu dhcpd: DHCPREQUEST for 192.168.0.203 (192.168.0.1) from 00:12:f0:8f:4c:24 (skankabilly) via ath0
Nov  6 19:17:22 ubuntu dhcpd: DHCPACK on 192.168.0.203 to 00:12:f0:8f:4c:24 (skankabilly) via ath0
Nov  6 19:17:37 ubuntu kernel: [81462.690709] Shorewall:INPUT:REJECT:IN=ath0 OUT= MAC=00:1d:6a:17:c4:2d:00:12:f0:8f:4c:24:08:00:45:00:0$
Nov  6 19:17:37 ubuntu dhcpd: DHCPRELEASE of 192.168.0.203 from 00:12:f0:8f:4c:24 (skankabilly) via ath0 (found)
Nov  6 19:17:38 ubuntu hostapd: ath0: STA 00:12:f0:8f:4c:24 IEEE 802.11: disassociated
Nov  6 19:28:19 ubuntu dibble: Shorewall restarted

```

Shorewall Confs

Interfaces
```
###############################################################################
#ZONE   INTERFACE       BROADCAST       OPTIONS
net     eth0            detect          dhcp,tcpflags,routefilter,nosmurfs,logmartians
loc     ath1            detect          tcpflags,nosmurfs
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE

```

Zones
```
###############################################################################
#ZONE   TYPE            OPTIONS         IN                      OUT
#                                       OPTIONS                 OPTIONS
fw      firewall
net     ipv4
loc     ipv4
#LAST LINE - ADD YOUR ENTRIES ABOVE THIS ONE - DO NOT REMOVE
```

Masq
```
###############################################################################
#INTERFACE              SOURCE          ADDRESS         PROTO   PORT(S) IPSEC   MARK
eth0                    ath0
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE

```

Rules
```
##############################################################################################################
#ACTION         SOURCE          DEST            PROTO   DEST    SOURCE          ORIGINAL        RATE            USER/   MARK
#                                                       PORT    PORT(S)         DEST            LIMIT           GROUP
#
#       Accept DNS connections from the firewall to the network
#
DNS/ACCEPT      $FW             net
#
#       Accept SSH connections from the local network for administration
#
ACCEPT          loc             $FW             tcp     4321
ACCEPT          loc             $FW             tcp     www
ACCEPT          net             $FW             tcp     4321
ACCEPT          net             $FW             tcp     www
#
#       Allow Ping from the local network
#
Ping/ACCEPT     loc             $FW
#
# Reject Ping from the "bad" net zone.. and prevent your log from being flooded..
#
Ping/REJECT     net             $FW
ACCEPT          $FW             loc             icmp
ACCEPT          $FW             net             icmp
#

#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE

```

Policy
```
###############################################################################
#SOURCE         DEST            POLICY          LOG LEVEL       LIMIT:BURST
# Policies for traffic originating from the local LAN (loc)
#
loc             net             ACCEPT
loc             $FW             ACCEPT
loc             all             REJECT          info

#
# Policies for traffic originating from the Firewall zone ($FW)
$FW             net             ACCEPT
$FW             loc             REJECT          info
$FW             all             REJECT          info

#
# Policies for traffic originating from the Internet zone (net)
#
net             $FW             DROP
net             loc             DROP            info
net             all             DROP            info

# THE FOLLOWING POLICY MUST BE LAST
all             all             REJECT          info

```

Thank you in advance. Any help would be greatly appreicated. Cheers.

-Sjokomunn

---

### Post by sjokomunn on 2008-11-17
Alright, it's working very well now folks. The only thing I needed to change in the above configuration (although I have also cleaned up the rules a fair bit) was the 'ath1' in the interfaces file. This should be 'ath0'. It took me way too long to notice this but at least it was an easy fix. Cheers.

---

### Post by pdc124 on 2008-11-21
im trying to do this as well - but to have a wired connection to the internet and provide an ad-hoc wireless network for a couple of clients.
Im starting with a default installation of ubuntu.
I can configure my Wireless card with a fixed ip address, and dnsmasq to give out IP addresses, but im having problems installing and configuring shorewall.
( ive done this in gentoo, with few problems )

my shorewall conf looks similar to yours - but hwow do i start shorewall -  dnsmasq runs from an init script . Shorewall doesnt seem to want to.
issuing sudo shorewall start
stops www connections on eth0 , though ping still works 

rphd@rphd-laptop:~$ grep ^[A-Za-z] /etc/shorewall/shorewall.conf 
STARTUP_ENABLED=Yes
VERBOSITY=1
SHOREWALL_COMPILER=
LOGFILE=/var/log/messages
LOGFORMAT="Shorewall:%s:%s:"
LOGTAGONLY=No
LOGRATE=
LOGBURST=
LOGALLNEW=
BLACKLIST_LOGLEVEL=
MACLIST_LOG_LEVEL=info
TCP_FLAGS_LOG_LEVEL=info
RFC1918_LOG_LEVEL=info
SMURF_LOG_LEVEL=info
LOG_MARTIANS=No
IPTABLES=
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/bin:/usr/local/sbin
SHOREWALL_SHELL=/bin/sh
SUBSYSLOCK=/var/lock/subsys/shorewall
MODULESDIR=
CONFIG_PATH=/etc/shorewall:/usr/share/shorewall
RESTOREFILE=
IPSECFILE=zones
LOCKFILE=
DROP_DEFAULT="Drop"
REJECT_DEFAULT="Reject"
ACCEPT_DEFAULT="none"
QUEUE_DEFAULT="none"
RSH_COMMAND='ssh ${root}@${system} ${command}'
RCP_COMMAND='scp ${files} ${root}@${system}:${destination}'
IP_FORWARDING=On
ADD_IP_ALIASES=Yes
ADD_SNAT_ALIASES=No
RETAIN_ALIASES=No
TC_ENABLED=Internal
TC_EXPERT=No
CLEAR_TC=Yes
MARK_IN_FORWARD_CHAIN=No
CLAMPMSS=No
ROUTE_FILTER=No
DETECT_DNAT_IPADDRS=No
MUTEX_TIMEOUT=60
ADMINISABSENTMINDED=Yes
BLACKLISTNEWONLY=Yes
DELAYBLACKLISTLOAD=No
MODULE_SUFFIX=
DISABLE_IPV6=Yes
BRIDGING=No
DYNAMIC_ZONES=No
PKTTYPE=Yes
RFC1918_STRICT=No
MACLIST_TABLE=filter
MACLIST_TTL=
SAVE_IPSETS=No
MAPOLDACTIONS=No
FASTACCEPT=No
IMPLICIT_CONTINUE=Yes
HIGH_ROUTE_MARKS=No
USE_ACTIONS=Yes
OPTIMIZE=1
EXPORTPARAMS=No
EXPAND_POLICIES=No
BLACKLIST_DISPOSITION=DROP
MACLIST_DISPOSITION=REJECT
TCP_FLAGS_DISPOSITION=DROP
rphd@rphd-laptop:~$ grep ^[A-Za-z] /etc/shorewall/zones
fw	firewall
net	ipv4
loc	ipv4
rphd@rphd-laptop:~$ grep ^[A-Za-z] /etc/shorewall/interfaces
net     eth0            detect          dhcp,tcpflags,routefilter,nosmurfs,logmartians
loc     eth1            detect          tcpflags,nosmurfs
rphd@rphd-laptop:~$ grep ^[A-Za-z] /etc/shorewall/masq
eth0                    eth1
rphd@rphd-laptop:~$ grep ^[A-Za-z] /etc/shorewall/policy
loc		net		ACCEPT
loc		$FW		ACCEPT		
loc		all		REJECT		info
net		$FW		DROP		info
net		loc		DROP		info
net		all		DROP		info
all		all		REJECT		info
rphd@rphd-laptop:~$ grep ^[A-Za-z] /etc/shorewall/rules
DNS/ACCEPT	$FW		net
SSH/ACCEPT	loc		$FW
Ping/ACCEPT	loc		$FW
Ping/REJECT	net		$FW
ACCEPT		$FW		loc		icmp
ACCEPT		$FW		net		icmp
Web/ACCEPT	net		fw		
Web/ACCEPT	net		loc		
rphd@rphd-laptop:~$

---

