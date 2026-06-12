---
title: "Load balancing two isp and two local"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by run_time on 2008-01-12
Hi, i'm trying to load balance two ISP's (DSL and Cable) and two local networks using the following script. It appears to work partially somehow. Thing is it always sends me trough the DSL line instead of the cable when it is needed. I static routed two IP's trough the cable but that's not working for me since i need a dynamic routing. Any ideas where the problem is with this script? I'm open to suggestions on other scripts too. 

```
#! /bin/sh
# Load balancing script by mambang
# using 4 nics, 2 isp, 2 lan segment
#
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
IFCONFIG=/sbin/ifconfig
IP=/sbin/ip
IPTABLES=/usr/sbin/iptables

#Device 1 connected to ISP1
DEV1=eth3
NET1=84.54.160.198
SUB1=84.54.160.0/30
GW1=84.54.160.197

#Device 2 connected to ISP2
DEV2=eth0
NET2=192.168.1.2
SUB2=192.168.1.0/24
GW2=192.168.1.1

#LAN device connected to LAN group1
DEV3=eth1
LAN1=192.168.0.1
SUB3=192.168.0.0/24

#LAN device connected to LAN group2
DEV4=eth2
LAN2=192.168.142.1
SUB4=192.168.142.0/24


#---------------------DO THIS MANUALLY------------
#echo "1 T1" >> /etc/$IProute2/rt_tables
#echo "2 T2" >> /etc/$IProute2/rt_tables
#-------------------------------------------------

START_ROUTING(){

#net

#segement1
$IP route add $SUB1 dev $DEV1 src $NET1 table T1
$IP route add $SUB3 dev $DEV3 src $LAN1 table T1
$IP route add default via $GW1 table T1

#segment2
$IP route add $SUB2 dev $DEV2 src $NET2 table T2
$IP route add $SUB4 dev $DEV4 src $LAN2 table T1
$IP route add default via $GW2 table T2

#rules for all segment
$IP rule add from $NET1 table T1
$IP rule add from $LAN1 table T1
$IP rule add from $NET2 table T2
$IP rule add from $LAN2 table T1

#using iptable to mark packets
$IPTABLES -t mangle -A OUTPUT --source $SUB3 -j MARK --set-mark 0x10
$IPTABLES -t mangle -A OUTPUT --source $SUB4 -j MARK --set-mark 0x20
$IPTABLES -t nat -A POSTROUTING -o $DEV1 -j SNAT --to-source=$NET1
$IPTABLES -t nat -A POSTROUTING -o $DEV2 -j SNAT --to-source=$NET2


#default gateway for other
$IP route add default via $GW1

#avoids incoming packets from rejected
echo 0 > /proc/sys/net/ipv4/conf/$DEV1/rp_filter
echo 0 > /proc/sys/net/ipv4/conf/$DEV2/rp_filter

# adding rule for fwmark
$IP rule add fwmark 0x10 pri 100 table T1
$IP rule add fwmark 0x20 pri 101 table T2

# make sure packets comes and returns using same route
ip rule add from $NET1 pri 200 table T1
ip rule add from $NET2 pri 300 table T2

}

BALANCING(){
#load balancing

#$IP route add default scope global nexthop via $GW1 dev $DEV1 weight 1 nexthop via $GW2 dev $DEV2 weight 1

$IP route replace default equalize \
        nexthop via $GW1 dev $DEV1 \
        nexthop via $GW2 dev $DEV2
}


#-------------flushes all route and rule-------------------
REMOVE_TABLE(){
ALLDEV="eth0|eth1|eth2|eth3|lo"
ALLTABLES="T1|T2"
keepers="dev ($ALLDEV)"
tables="lookup ($ALLTABLES)"


echo
echo ***Before
echo "Rules..."
$IP ru sh
echo""
echo "Routes..."
$IP ro sh
echo "Rules for table T1..."
$IP ro sh table T1
echo""
echo "Rules for table T2..."
$IP ro sh table T2
echo""
$IP route delete default &>/dev/null
$IP route show | awk -v k="$keepers" '$0 !~ k \
    { print " $IP route delete " $0 | "bash" }'
for wan in ${ALLTABLES//|/ }; do
  $IP route flush table $wan &>/dev/null
done

$IP rule show | awk -v k="$tables" '$0 ~ k \
    { sub(/from all/,""); print "ip rule del " substr($0, 5) | "bash" }'
echo ""

$IP rule show | awk -v k="$tables" '$0 ~ k \
    { sub(/from all/,""); print "ip rule del " substr($0, 7) | "bash" }'
echo ""
echo "ALL Tables and Rules Deleted"

echo "Adding default gateway ....."
$IP route add default via $GW1

$IP route flush cache
echo
echo "***After"
echo "Rules..."
$IP ru sh
echo "Routes..."
$IP ro sh
echo "Rules for table T1..."
$IP ro sh table T1
echo "Rules for table T2..."
$IP ro sh table T2
}


case "$1" in
  start)
        echo "Creating new routing tables ....."
        START_ROUTING
        echo "Start load balancing rules ....."
        BALANCING
        echo "DONE....New routing has been added."
        #Flush routing cache
        $IP route flush cache
        ;;
 stop)
        REMOVE_TABLE
        echo "DONE....Default routing has been restore."
        echo ""
        echo "Flushing iptables mangle rules ....:"
        $IPTABLES -F -t mangle
        echo "DONE"
        ;;
  *)
        N=/etc/init.d/splitgateway
        echo "Cara Guna: $N {start|stop}" >&2
        exit 1
        ;;
esac

exit 0
```

---

