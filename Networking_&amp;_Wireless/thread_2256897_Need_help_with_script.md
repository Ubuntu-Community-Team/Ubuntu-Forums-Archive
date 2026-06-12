---
title: "Need help with script"
date: 2014-12-15
forum: Networking &amp; Wireless
---

### Post by nomac29 on 2014-12-15
Ok, this is not a problem directly related to ubuntu, as i'm having trouble with the firmware on my router. But i'm running out of ideas where and who to ask for help..

I got an Asus RT-56U, an ARM based router, with Asus Merlin firmware installed, which is linux based :)
I'm fairly new when it comes to linux and advanced networking, so hope  i could get some help here, didn't get much feedback on the firmware  forums..

I'm trying to setup a connection on the router to my cisco vpn provider, where i need to use vpnc.
They handed me a script, which i'm trying to run, but i got a few issues trying so.. Here's the original script: [https://www.beevpn.com/guides/Router/DD-WRT](https://www.beevpn.com/guides/Router/DD-WRT)

I  think theres some path issues, but i'm really not sure what to look  for, first of all i'm trying to understand how the different commands  work..

When i run the script (with the -x option) it looks like this:

```

admin@RT-AC56U-3A10:/tmp/home/root# sh -x /jffs/scripts/services-start

+ mkdir -p /tmp/etc/vpnc
+ rm -f /tmp/etc/vpnc/vpnc.sh
+ echo
#!/bin/sh

logger -t $(basename $0) "started [$@]"

vpn_concentrator="signon1.beevpn.com"
vpn_keepalive_host1="217.15.175.65"
vpn_groupname="beevpn"
vpn_grouppasswd="beecustomer"
vpn_username="xxxx" ##enter your username here
vpn_password="xxxx" ##enter your password here

#--do not edit this--
#Written by Alain R. 28.Sep.2007, and fixed/adapted by BeeVPN 13.May.2012
vpnc-disconnect
rm -f /tmp/etc/vpnc/vpn.conf
echo "
IPSec gateway $vpn_concentrator
IPSec ID $vpn_groupname
IPSec secret $vpn_grouppasswd
Xauth username $vpn_username
Xauth password $vpn_password
" >> /tmp/etc/vpnc/vpn.conf
DEFAULT_ROUTE_BACKUP="/tmp/vpnc-default-route-backup"
DEFAULT_RESOLV_BACKUP="/tmp/vpnc-default-resolv-backup"
pingtest1 () {
ping -w 5 -q -c2 $param1 >> /dev/null
if [ "$?" == "0" ]; then
echo 0 #reachable
else
echo 1 #not reachable
fi
}

iptablesdone="0"

restore_routing() {
if [ -f $DEFAULT_ROUTE_BACKUP ]; then
if [ "`ip route |grep default`" == "" ]; then
ip route add `cat "$DEFAULT_ROUTE_BACKUP"`
else
ip route replace `cat "$DEFAULT_ROUTE_BACKUP"`
fi
fi
}

restore_everything() {
tundev="`ifconfig |grep tun |cut -b 1-4`"
vpnc-disconnect
restore_routing
if [ "$iptablesdone" == "1" ]; then
iptables -D FORWARD -o $tundev -j ACCEPT
iptables -D FORWARD -i $tundev -j ACCEPT
iptables -t nat -D POSTROUTING -o $tundev -j MASQUERADE
iptablesone="0";
fi
if [ -f $DEFAULT_RESOLV_BACKUP ]; then
cat $DEFAULT_RESOLV_BACKUP > /tmp/etc/vpnc/resolv.dnsmasq.tmp
killall dnsmasq
cat /tmp/etc/vpnc/resolv.dnsmasq.tmp > /tmp/resolv.dnsmasq
dnsmasq --conf-file=/tmp/dnsmasq.conf
fi
}

if [ ! -f $DEFAULT_ROUTE_BACKUP ]; then
rm $DEFAULT_ROUTE_BACKUP
ip route| grep ^default > $DEFAULT_ROUTE_BACKUP
fi
if [ ! -f $DEFAULT_RESOLV_BACKUP ]; then
cp /etc/resolv.conf $DEFAULT_RESOLV_BACKUP
fi

while [ true ]; do
param1=$vpn_concentrator;
if [ "`pingtest1`" == "0" ]; then
doloop=1;
while [ $doloop -gt 0 ]; do
param1=$vpn_keepalive_host1;
if [ "`pingtest1`" == "0" ]; then
sleep 300
else
doloop=0;
vpnc-disconnect
restore_everything
vpnc /tmp/etc/vpnc/vpn.conf --dpd-idle 0
sleep 1
if [ "`pingtest1`" != "0" ]; then
sleep 10
fi
if [ "$iptablesdone" == "0" ]; then
tundev="`ifconfig |grep tun |cut -b 1-4`"
iptables -A FORWARD -o $tundev -j ACCEPT
iptables -A FORWARD -i $tundev -j ACCEPT
iptables -t nat -A POSTROUTING -o $tundev -j MASQUERADE
iptablesone="1";
fi
cat /tmp/resolv.conf > /tmp/etc/vpnc/resolv.dnsmasq.tmp
killall dnsmasq
cat /tmp/etc/vpnc/resolv.dnsmasq.tmp > /tmp/resolv.dnsmasq
dnsmasq --conf-file=/tmp/dnsmasq.conf
sleep 9
fi
done
else
restore_routing
sleep 10;
fi
done

return 0;

+ chmod a+rx /tmp/etc/vpnc/vpnc.sh
+ sh -x /tmp/etc/vpnc/vpnc.sh
+ basename /tmp/etc/vpnc/vpnc.sh
+ logger -t vpnc.sh started []
+ vpn_concentrator=signon1.beevpn.com
+ vpn_keepalive_host1=217.15.175.65
+ vpn_groupname=beevpn
+ vpn_grouppasswd=beecustomer
+ vpn_username=xxxx
+ vpn_password=xxxx
+ vpnc-disconnect
no vpnc found running
+ rm -f /tmp/etc/vpnc/vpn.conf
+ echo
IPSec gateway signon1.beevpn.com
IPSec ID beevpn
IPSec secret beecustomer
Xauth username xxxx
Xauth password xxxx

+ DEFAULT_ROUTE_BACKUP=/tmp/vpnc-default-route-backup
+ DEFAULT_RESOLV_BACKUP=/tmp/vpnc-default-resolv-backup
+ iptablesdone=0
+ [ ! -f /tmp/vpnc-default-route-backup ]
+ rm /tmp/vpnc-default-route-backup
rm: can't remove '/tmp/vpnc-default-route-backup': No such file or directory
+ ip route
+ grep ^default
+ [ ! -f /tmp/vpnc-default-resolv-backup ]
+ cp /etc/resolv.conf /tmp/vpnc-default-resolv-backup
+ [ true ]
+ param1=signon1.beevpn.com
+ pingtest1
+ ping -w 5 -q -c2 signon1.beevpn.com
+ [ 0 == 0 ]
+ echo 0
+ [ 0 == 0 ]
+ doloop=1
+ [ 1 -gt 0 ]
+ param1=217.15.175.65
+ pingtest1
+ ping -w 5 -q -c2 217.15.175.65
+ [ 1 == 0 ]
+ echo 1
+ [ 1 == 0 ]
+ doloop=0
+ vpnc-disconnect
no vpnc found running
+ restore_everything
+ ifconfig
+ grep tun
+ cut -b 1-4
+ tundev=
+ vpnc-disconnect
no vpnc found running
+ restore_routing
+ [ -f /tmp/vpnc-default-route-backup ]
+ ip route
+ grep default
+ [ default via 2.104.117.1 dev eth0  ==  ]
+ cat /tmp/vpnc-default-route-backup
+ ip route replace default via 2.104.117.1 dev eth0
+ [ 0 == 1 ]
+ [ -f /tmp/vpnc-default-resolv-backup ]
+ cat /tmp/vpnc-default-resolv-backup
+ killall dnsmasq
+ cat /tmp/etc/vpnc/resolv.dnsmasq.tmp
+ dnsmasq --conf-file=/tmp/dnsmasq.conf

dnsmasq: cannot read /tmp/dnsmasq.conf: No such file or directory
+ vpnc /tmp/etc/vpnc/vpn.conf --dpd-idle 0
unknown host `signon1.beevpn.com'

+ sleep 1
+ pingtest1
+ ping -w 5 -q -c2 217.15.175.65
+ [ 1 == 0 ]
+ echo 1
+ [ 1 != 0 ]
+ sleep 10
+ [ 0 == 0 ]
+ ifconfig
+ grep tun
+ cut -b 1-4
+ tundev=
+ iptables -A FORWARD -o -j ACCEPT
Bad argument `ACCEPT'
Try `iptables -h' or 'iptables --help' for more information.
+ iptables -A FORWARD -i -j ACCEPT
Bad argument `ACCEPT'
Try `iptables -h' or 'iptables --help' for more information.
+ iptables -t nat -A POSTROUTING -o -j MASQUERADE
Bad argument `MASQUERADE'
Try `iptables -h' or 'iptables --help' for more information.
+ iptablesone=1
+ cat /tmp/resolv.conf
+ killall dnsmasq
killall: dnsmasq: no process killed
+ cat /tmp/etc/vpnc/resolv.dnsmasq.tmp
+ dnsmasq --conf-file=/tmp/dnsmasq.conf

dnsmasq: cannot read /tmp/dnsmasq.conf: No such file or directory
+ sleep 9
+ [ 0 -gt 0 ]
+ [ true ]
+ param1=signon1.beevpn.com
+ pingtest1
+ ping -w 5 -q -c2 signon1.beevpn.com
ping: bad address 'signon1.beevpn.com'
+ [ 1 == 0 ]
+ echo 1
+ [ 1 == 0 ]
+ restore_routing
+ [ -f /tmp/vpnc-default-route-backup ]
+ ip route
+ grep default
+ [ default via 2.104.117.1 dev eth0  ==  ]
+ cat /tmp/vpnc-default-route-backup
+ ip route replace default via 2.104.117.1 dev eth0
+ sleep 10

^C
admin@RT-AC56U-3A10:/tmp/home/root#



```

Somehow  it can't resolve the hostname signon1.beevpn, which i think is a basic  problem in all this. But if i use the ip address instead of name, it seems to work..
Also, the "cannot read /tmp/dnsmasq.conf: No such file or directory" - error. I got a dnsmasq.conf in /etc, not in /tmp. But i don't know if it's supposed to point to this one, or the script is supposed to create the one in /tmp..
So if i edit the script to use the ip and point dnsmasq to /etc instead, it looks like this:

```

ASUSWRT-Merlin RT-AC56U_3.0.0.4 Sat Nov  8 02:23:13 UTC 2014
admin@RT-AC56U-3A10:/tmp/home/root# sh -x /jffs/scripts/services-start
+ mkdir -p /tmp/etc/vpnc
+ rm -f /tmp/etc/vpnc/vpnc.sh
+ echo
#!/bin/sh

logger -t $(basename $0) "started [$@]"

vpn_concentrator="217.15.175.1"
vpn_keepalive_host1="217.15.175.65"
vpn_groupname="beevpn"
vpn_grouppasswd="beecustomer"
vpn_username="xxxx" ##enter your username here
vpn_password="xxxx" ##enter your password here

#--do not edit this--
#Written by Alain R. 28.Sep.2007, and fixed/adapted by BeeVPN 13.May.2012
vpnc-disconnect
rm -f /tmp/etc/vpnc/vpn.conf
echo "
IPSec gateway $vpn_concentrator
IPSec ID $vpn_groupname
IPSec secret $vpn_grouppasswd
Xauth username $vpn_username
Xauth password $vpn_password
" >> /tmp/etc/vpnc/vpn.conf
DEFAULT_ROUTE_BACKUP="/tmp/vpnc-default-route-backup"
DEFAULT_RESOLV_BACKUP="/tmp/vpnc-default-resolv-backup"
pingtest1 () {
ping -w 5 -q -c2 $param1 >> /dev/null
if [ "$?" == "0" ]; then
echo 0 #reachable
else
echo 1 #not reachable
fi
}

iptablesdone="0"

restore_routing() {
if [ -f $DEFAULT_ROUTE_BACKUP ]; then
if [ "`ip route |grep default`" == "" ]; then
ip route add `cat "$DEFAULT_ROUTE_BACKUP"`
else
ip route replace `cat "$DEFAULT_ROUTE_BACKUP"`
fi
fi
}

restore_everything() {
tundev="`ifconfig |grep tun |cut -b 1-4`"
vpnc-disconnect
restore_routing
if [ "$iptablesdone" == "1" ]; then
iptables -D FORWARD -o $tundev -j ACCEPT
iptables -D FORWARD -i $tundev -j ACCEPT
iptables -t nat -D POSTROUTING -o $tundev -j MASQUERADE
iptablesone="0";
fi
if [ -f $DEFAULT_RESOLV_BACKUP ]; then
cat $DEFAULT_RESOLV_BACKUP > /tmp/etc/vpnc/resolv.dnsmasq.tmp
killall dnsmasq
cat /tmp/etc/vpnc/resolv.dnsmasq.tmp > /tmp/resolv.dnsmasq
dnsmasq --conf-file=/etc/dnsmasq.conf
fi
}

if [ ! -f $DEFAULT_ROUTE_BACKUP ]; then
rm $DEFAULT_ROUTE_BACKUP
ip route| grep ^default > $DEFAULT_ROUTE_BACKUP
fi
if [ ! -f $DEFAULT_RESOLV_BACKUP ]; then
cp /etc/resolv.conf $DEFAULT_RESOLV_BACKUP
fi

while [ true ]; do
param1=$vpn_concentrator;
if [ "`pingtest1`" == "0" ]; then
doloop=1;
while [ $doloop -gt 0 ]; do
param1=$vpn_keepalive_host1;
if [ "`pingtest1`" == "0" ]; then
sleep 300
else
doloop=0;
vpnc-disconnect
restore_everything
vpnc /tmp/etc/vpnc/vpn.conf --dpd-idle 0
sleep 1
if [ "`pingtest1`" != "0" ]; then
sleep 10
fi
if [ "$iptablesdone" == "0" ]; then
tundev="`ifconfig |grep tun |cut -b 1-4`"
iptables -A FORWARD -o $tundev -j ACCEPT
iptables -A FORWARD -i $tundev -j ACCEPT
iptables -t nat -A POSTROUTING -o $tundev -j MASQUERADE
iptablesone="1";
fi
cat /tmp/resolv.conf > /tmp/etc/vpnc/resolv.dnsmasq.tmp
killall dnsmasq
cat /tmp/etc/vpnc/resolv.dnsmasq.tmp > /tmp/resolv.dnsmasq
dnsmasq --conf-file=/etc/dnsmasq.conf
sleep 9
fi
done
else
restore_routing
sleep 10;
fi
done

return 0;

+ chmod a+rx /tmp/etc/vpnc/vpnc.sh
+ sh -x /tmp/etc/vpnc/vpnc.sh
+ basename /tmp/etc/vpnc/vpnc.sh
+ logger -t vpnc.sh started []
+ vpn_concentrator=217.15.175.1
+ vpn_keepalive_host1=217.15.175.65
+ vpn_groupname=beevpn
+ vpn_grouppasswd=beecustomer
+ vpn_username=xxxx
+ vpn_password=xxxx
+ vpnc-disconnect
no vpnc found running
+ rm -f /tmp/etc/vpnc/vpn.conf
+ echo
IPSec gateway 217.15.175.1
IPSec ID beevpn
IPSec secret beecustomer
Xauth username xxxx
Xauth password xxxx

+ DEFAULT_ROUTE_BACKUP=/tmp/vpnc-default-route-backup
+ DEFAULT_RESOLV_BACKUP=/tmp/vpnc-default-resolv-backup
+ iptablesdone=0
+ [ ! -f /tmp/vpnc-default-route-backup ]
+ [ ! -f /tmp/vpnc-default-resolv-backup ]
+ [ true ]
+ param1=217.15.175.1
+ pingtest1
+ ping -w 5 -q -c2 217.15.175.1
+ [ 0 == 0 ]
+ echo 0
+ [ 0 == 0 ]
+ doloop=1
+ [ 1 -gt 0 ]
+ param1=217.15.175.65
+ pingtest1
+ ping -w 5 -q -c2 217.15.175.65
+ [ 1 == 0 ]
+ echo 1
+ [ 1 == 0 ]
+ doloop=0
+ vpnc-disconnect
no vpnc found running
+ restore_everything
+ ifconfig
+ grep tun
+ cut -b 1-4
+ tundev=
+ vpnc-disconnect
no vpnc found running
+ restore_routing
+ [ -f /tmp/vpnc-default-route-backup ]
+ ip route
+ grep default
+ [ default via 2.104.117.1 dev eth0  ==  ]
+ cat /tmp/vpnc-default-route-backup
+ ip route replace default via 2.104.117.1 dev eth0
+ [ 0 == 1 ]
+ [ -f /tmp/vpnc-default-resolv-backup ]
+ cat /tmp/vpnc-default-resolv-backup
+ killall dnsmasq
killall: dnsmasq: no process killed
+ cat /tmp/etc/vpnc/resolv.dnsmasq.tmp
+ dnsmasq --conf-file=/etc/dnsmasq.conf
+ vpnc /tmp/etc/vpnc/vpn.conf --dpd-idle 0
/opt/etc/vpnc/vpnc-script: line 527: seq: not found
/opt/etc/vpnc/vpnc-script: line 527: can't create /etc/resolv.conf: Read-only fi
le system
VPNC started in background (pid: 1693)...
+ sleep 1
+ pingtest1
+ ping -w 5 -q -c2 217.15.175.65
+ [ 0 == 0 ]
+ echo 0
+ [ 0 != 0 ]
+ [ 0 == 0 ]
+ ifconfig
+ grep tun
+ cut -b 1-4
+ tundev=tun0
+ iptables -A FORWARD -o tun0 -j ACCEPT
+ iptables -A FORWARD -i tun0 -j ACCEPT
+ iptables -t nat -A POSTROUTING -o tun0 -j MASQUERADE
+ iptablesone=1
+ cat /tmp/resolv.conf
+ killall dnsmasq
+ cat /tmp/etc/vpnc/resolv.dnsmasq.tmp
+ dnsmasq --conf-file=/etc/dnsmasq.conf
+ sleep 9
+ [ 0 -gt 0 ]
+ [ true ]
+ param1=217.15.175.1
+ pingtest1
+ ping -w 5 -q -c2 217.15.175.1
+ [ 1 == 0 ]
+ echo 1
+ [ 1 == 0 ]
+ restore_routing
+ [ -f /tmp/vpnc-default-route-backup ]
+ ip route
+ grep default
+ [ default dev tun0  scope link  ==  ]
+ cat /tmp/vpnc-default-route-backup
+ ip route replace default via 2.104.117.1 dev eth0
+ sleep 10
^C
admin@RT-AC56U-3A10:/tmp/home/root#
```

I got a feeling i'm messing it up even more and my "fixes" aren't really fixes, but just creating other issues...

Also the resolv.conf error. I got a resolv.conf in /etc, which is a symlink to a read-only one in /rom/etc.. I'm really uncertain as to what is supposed to happen here, so i don't really know how to troubleshoot :(

---

### Post by nomac29 on 2014-12-15
Just ran a few diagnostic commands before and after the script is run:

**Before:**
```

admin@RT-AC56U-3A10:/tmp/home/root# **[COLOR=#ff0000]ifconfig -a[/COLOR]**

br0        Link encap:Ethernet  HWaddr BC:EE:7B:8F:3A:10
           inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:138609 errors:0 dropped:0 overruns:0 frame:0
           TX packets:88103 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:17359239 (16.5 MiB)  TX bytes:41404885 (39.4 MiB)

eth0       Link encap:Ethernet  HWaddr BC:EE:7B:8F:3A:10
           inet addr:2.104.117.116  Bcast:2.104.117.255  Mask:255.255.255.0
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:1504275 errors:0 dropped:0 overruns:0 frame:0
           TX packets:337024 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:464727047 (443.1 MiB)  TX bytes:98267851 (93.7 MiB)
           Interrupt:179 Base address:0x4000

eth1       Link encap:Ethernet  HWaddr BC:EE:7B:8F:3A:10
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:103812 errors:0 dropped:0 overruns:0 frame:2807778
           TX packets:180892 errors:88 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:56164840 (53.5 MiB)  TX bytes:121112007 (115.5 MiB)
           Interrupt:163

eth2       Link encap:Ethernet  HWaddr BC:EE:7B:8F:3A:14
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:185395 errors:0 dropped:0 overruns:0 frame:9043
           TX packets:331484 errors:90 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:30069558 (28.6 MiB)  TX bytes:322130048 (307.2 MiB)
           Interrupt:169

lo         Link encap:Local Loopback
           inet addr:127.0.0.1  Mask:255.0.0.0
           UP LOOPBACK RUNNING MULTICAST  MTU:16436  Metric:1
           RX packets:58460 errors:0 dropped:0 overruns:0 frame:0
           TX packets:58460 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:13255399 (12.6 MiB)  TX bytes:13255399 (12.6 MiB)

vlan1      Link encap:Ethernet  HWaddr BC:EE:7B:8F:3A:10
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:3886 errors:0 dropped:0 overruns:0 frame:0
           TX packets:74938 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:682095 (666.1 KiB)  TX bytes:16169432 (15.4 MiB)

vlan2      Link encap:Ethernet  HWaddr BC:EE:7B:8F:3A:10
           BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
           
           
admin@RT-AC56U-3A10:/tmp/home/root# [COLOR=#ff0000]**ip add**[/COLOR]
1: lo: <LOOPBACK,MULTICAST,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 brd 127.255.255.255 scope host lo
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether bc:ee:7b:8f:3a:10 brd ff:ff:ff:ff:ff:ff
    inet 2.104.117.116/24 brd 2.104.117.255 scope global eth0
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether bc:ee:7b:8f:3a:10 brd ff:ff:ff:ff:ff:ff
4: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether bc:ee:7b:8f:3a:14 brd ff:ff:ff:ff:ff:ff
5: vlan1@eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP
    link/ether bc:ee:7b:8f:3a:10 brd ff:ff:ff:ff:ff:ff
6: vlan2@eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN
    link/ether bc:ee:7b:8f:3a:10 brd ff:ff:ff:ff:ff:ff
7: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN
    link/ether bc:ee:7b:8f:3a:10 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.1/24 brd 192.168.1.255 scope global br0
    
    
admin@RT-AC56U-3A10:/tmp/home/root# [COLOR=#ff0000]**ip route**[/COLOR]
217.15.175.1 via 2.104.117.1 dev eth0
2.104.117.1 dev eth0  scope link
192.168.1.0/24 dev br0  proto kernel  scope link  src 192.168.1.1
2.104.117.0/24 dev eth0  proto kernel  scope link  src 2.104.117.116
127.0.0.0/8 dev lo  scope link
default via 2.104.117.1 dev eth0


admin@RT-AC56U-3A10:/tmp/home/root# [COLOR=#ff0000]**iptables -L -n**[/COLOR]
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
DROP       all  --  0.0.0.0/0            0.0.0.0/0            state INVALID
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state NEW
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
DROP       all  --  0.0.0.0/0            0.0.0.0/0
DROP       all  --  0.0.0.0/0            0.0.0.0/0            state INVALID
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
DROP       icmp --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate DNAT
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain FUPNP (0 references)
target     prot opt source               destination

Chain PControls (0 references)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0

Chain logaccept (0 references)
target     prot opt source               destination
LOG        all  --  0.0.0.0/0            0.0.0.0/0            state NEW LOG flags 7 level 4 prefix "ACCEPT "
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0

Chain logdrop (0 references)
target     prot opt source               destination
LOG        all  --  0.0.0.0/0            0.0.0.0/0            state NEW LOG flags 7 level 4 prefix "DROP "
DROP       all  --  0.0.0.0/0            0.0.0.0/0
admin@RT-AC56U-3A10:/tmp/home/root#

```

**After:**
```


admin@RT-AC56U-3A10:/tmp/home/root# [COLOR=#ff0000]**ifconfig -a**[/COLOR]
br0        Link encap:Ethernet  HWaddr BC:EE:7B:8F:3A:10
           inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:140623 errors:0 dropped:0 overruns:0 frame:0
           TX packets:89372 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:17586062 (16.7 MiB)  TX bytes:41686081 (39.7 MiB)

eth0       Link encap:Ethernet  HWaddr BC:EE:7B:8F:3A:10
           inet addr:2.104.117.116  Bcast:2.104.117.255  Mask:255.255.255.0
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:1572180 errors:0 dropped:0 overruns:0 frame:0
           TX packets:358264 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:541593749 (516.5 MiB)  TX bytes:100094607 (95.4 MiB)
           Interrupt:179 Base address:0x4000

eth1       Link encap:Ethernet  HWaddr BC:EE:7B:8F:3A:10
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:111532 errors:0 dropped:0 overruns:0 frame:2820489
           TX packets:193103 errors:89 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:56744285 (54.1 MiB)  TX bytes:138276804 (131.8 MiB)
           Interrupt:163

eth2       Link encap:Ethernet  HWaddr BC:EE:7B:8F:3A:14
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:198659 errors:0 dropped:0 overruns:0 frame:9317
           TX packets:372464 errors:91 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:31261339 (29.8 MiB)  TX bytes:380807038 (363.1 MiB)
           Interrupt:169

lo         Link encap:Local Loopback
           inet addr:127.0.0.1  Mask:255.0.0.0
           UP LOOPBACK RUNNING MULTICAST  MTU:16436  Metric:1
           RX packets:59118 errors:0 dropped:0 overruns:0 frame:0
           TX packets:59118 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:13395947 (12.7 MiB)  TX bytes:13395947 (12.7 MiB)

tun0       Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-0
0-00
           inet addr:217.15.160.9  P-t-P:217.15.160.9  Mask:255.255.255.255
           UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
           RX packets:4 errors:0 dropped:0 overruns:0 frame:0
           TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:500
           RX bytes:386 (386.0 B)  TX bytes:864 (864.0 B)

vlan1      Link encap:Ethernet  HWaddr BC:EE:7B:8F:3A:10
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:3886 errors:0 dropped:0 overruns:0 frame:0
           TX packets:75804 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:682095 (666.1 KiB)  TX bytes:16299743 (15.5 MiB)

vlan2      Link encap:Ethernet  HWaddr BC:EE:7B:8F:3A:10
           BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
           

admin@RT-AC56U-3A10:/tmp/home/root# [COLOR=#ff0000]**ip add**[/COLOR]
1: lo: <LOOPBACK,MULTICAST,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 brd 127.255.255.255 scope host lo
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNO
WN qlen 1000
    link/ether bc:ee:7b:8f:3a:10 brd ff:ff:ff:ff:ff:ff
    inet 2.104.117.116/24 brd 2.104.117.255 scope global eth0
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNO
WN qlen 1000
    link/ether bc:ee:7b:8f:3a:10 brd ff:ff:ff:ff:ff:ff
4: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNO
WN qlen 1000
    link/ether bc:ee:7b:8f:3a:14 brd ff:ff:ff:ff:ff:ff
5: vlan1@eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP
    link/ether bc:ee:7b:8f:3a:10 brd ff:ff:ff:ff:ff:ff
6: vlan2@eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN
    link/ether bc:ee:7b:8f:3a:10 brd ff:ff:ff:ff:ff:ff
7: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN
    link/ether bc:ee:7b:8f:3a:10 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.1/24 brd 192.168.1.255 scope global br0
11: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1412 qdisc pfifo_fast st
ate UNKNOWN qlen 500
    link/none
    inet 217.15.160.9/32 scope global tun0
    
    
admin@RT-AC56U-3A10:/tmp/home/root# **[COLOR=#ff0000]ip route[/COLOR]**
217.15.160.9 dev tun0  scope link
217.15.175.1 via 2.104.117.1 dev eth0  src 2.104.117.116  mtu 1500 advmss 1460
2.104.117.1 dev eth0  scope link
192.168.1.0/24 dev br0  proto kernel  scope link  src 192.168.1.1
2.104.117.0/24 dev eth0  proto kernel  scope link  src 2.104.117.116
127.0.0.0/8 dev lo  scope link
default dev tun0  scope link


admin@RT-AC56U-3A10:/tmp/home/root# **[COLOR=#ff0000]iptables -L -n[/COLOR]**
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
DROP       all  --  0.0.0.0/0            0.0.0.0/0            state INVALID
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTA
BLISHED
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state NEW
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            state RELATED,ESTA
BLISHED
DROP       all  --  0.0.0.0/0            0.0.0.0/0
DROP       all  --  0.0.0.0/0            0.0.0.0/0            state INVALID
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
DROP       icmp --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate DNAT
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain FUPNP (0 references)
target     prot opt source               destination

Chain PControls (0 references)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0

Chain logaccept (0 references)
target     prot opt source               destination
LOG        all  --  0.0.0.0/0            0.0.0.0/0            state NEW LOG flag
s 7 level 4 prefix "ACCEPT "
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0

Chain logdrop (0 references)
target     prot opt source               destination
LOG        all  --  0.0.0.0/0            0.0.0.0/0            state NEW LOG flag
s 7 level 4 prefix "DROP "
DROP       all  --  0.0.0.0/0            0.0.0.0/0
admin@RT-AC56U-3A10:/tmp/home/root#
```

Don't know if this helps, but hope so :)

---

### Post by nomac29 on 2014-12-16
Please, anyone?!?

---

