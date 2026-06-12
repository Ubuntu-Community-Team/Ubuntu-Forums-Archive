---
title: "UDP broadcast forwarding"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by Gyuszk on 2007-01-10
Hello netfilter users and developers,

   I have an interesting problem to solve with netfilter. I'm running a Linux server box with two ethernet interfaces. "eth0" is the primary interface, it is connected to a local LAN (but gets public and fix internet ip address) in the building, and eth1 is the secondary interface connected to the local LAN network (in the room).
Details:

eth0      Link encap:Ethernet  HWaddr 00:04:E2:EB:8E:56
         inet addr:193.xxx.xxx.31  Bcast:193.225.227.255  Mask:255.255.255.0
         inet6 addr: xxx::xxx:e2ff:feeb:8e56/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth1      Link encap:Ethernet  HWaddr 00:48:54:6E:B3:EA
         inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
         inet6 addr: xxx::xxx:54ff:fe6e:b3ea/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

   
My big problem is: there is a game server on the top-local network (with address 193.225.227.xxx, in the building somewhere), that I cannot connect to by hand in the actual game, it is only acceptable in the game's "local server browser" application. The game has a little console that cannot be used for manual connecting, nor the game has an option for that. If there would be, there would be no problems, as I can reach and ping that machine.
   This game (the client) broadcasts  packages to 255.255.255.255, protocol UDP, source port random, destination port 27015, 27016, 27017, 27018, 27019, 27020, for finding servers on the local network. The computers in the room are all behind this Linux server I described above, all others are off. If the packages are broadcasted against 255.255.255.255, these broadcasted UDP packages will never reache the machines on the "top" LAN. You can figure out the network's topology from the "ifconfig" output.
My big problem to solve is: can this UDP broadcasting be forwarded from "eth1" (local) to "eth0" (top lan)?

Any help or suggestion is welcome.
Thanks in advance.

My iptables configuration script:

###

IPT="/sbin/iptables"
IPTS="/sbin/iptables-save"
IPTR="/sbin/iptables-restore"

INET_IFACE="eth0"

LOCAL_IFACE="eth1"
LOCAL_IP="192.168.0.1"
LOCAL_NET="192.168.0.0/8"
LOCAL_BCAST="255.255.255.0"

LO_IFACE="lo"
LO_IP="127.0.0.1"

if [ "$1" = "save" ]
then
   echo -n "Saving firewall settings: /etc/netfilter/iptables ... "
   $IPTS > /etc/netfilter/iptables
   echo "done"
   exit 0
elif [ "$1" = "restore" ]
then
   echo -n "Restoring firewall settings: /etc/netfilter/iptables ... "
   $IPTR < /etc/netfilter/iptables
   echo "done"
   exit 0
fi

echo "Loading kernel modules ..."

/sbin/depmod -a
/sbin/modprobe ip_tables
/sbin/modprobe ip_conntrack
/sbin/modprobe iptable_nat
/sbin/modprobe ipt_MASQUERADE
/sbin/modprobe iptable_filter
/sbin/modprobe ipt_state
/sbin/modprobe ipt_LOG

echo "1" > /proc/sys/net/ipv4/ip_forward
echo "1" > /proc/sys/net/ipv4/conf/all/rp_filter

echo "Setting all rules to accept ..."

$IPT -P INPUT ACCEPT
$IPT -P FORWARD ACCEPT
$IPT -P OUTPUT ACCEPT
$IPT -t nat -P PREROUTING ACCEPT
$IPT -t nat -P POSTROUTING ACCEPT
$IPT -t nat -P OUTPUT ACCEPT
$IPT -t mangle -P PREROUTING ACCEPT
$IPT -t mangle -P OUTPUT ACCEPT

$IPT -F
$IPT -t nat -F
$IPT -t mangle -F

$IPT -X
$IPT -t nat -X
$IPT -t mangle -X

if [ "$1" = "stop" ]
then
   echo "All denying rules deleted. Security is no more the case."
   exit 0
fi
echo "Denying all connections in, out, and forward. All packages are killed silently."
$IPT -P INPUT DROP
$IPT -P OUTPUT DROP
$IPT -P FORWARD DROP
echo ".. succeed. From now on, if you want any network activity, you'll have to permit it explicitly."

echo "Creating custom chains ..."

$IPT -N bad_packets
$IPT -N bad_tcp_packets
$IPT -N icmp_packets
$IPT -N udp_inbound
$IPT -N udp_outbound
$IPT -N tcp_inbound
$IPT -N tcp_outbound

$IPT -A bad_packets -p ALL -m state --state INVALID -j LOG --log-prefix "Invalid package: "
$IPT -A bad_packets -p ALL -m state --state INVALID -j DROP
$IPT -A bad_packets -p tcp -j bad_tcp_packets
$IPT -A bad_packets -p ALL -j RETURN
$IPT -A bad_tcp_packets -p tcp -i $LOCAL_IFACE -j RETURN
$IPT -A bad_tcp_packets -p tcp ! --syn -m state --state NEW -j LOG --log-prefix "Uj kapcsolat, nem syn:"
$IPT -A bad_tcp_packets -p tcp ! --syn -m state --state NEW -j DROP
$IPT -A bad_tcp_packets -p tcp -j RETURN

$IPT -A icmp_packets -p ICMP -s 0/0 --icmp-type 8 -j ACCEPT
$IPT -A icmp_packets -p ICMP -s 0/0 --icmp-type 11 -j ACCEPT
$IPT -A icmp_packets -p ICMP -j RETURN

$IPT -A udp_inbound -p UDP -s 0/0 --destination-port 3997 -j ACCEPT
$IPT -A udp_inbound -p UDP -s 0/0 --destination-port 3998 -j ACCEPT
$IPT -A udp_inbound -p UDP -s 0/0 --destination-port 27005 -j ACCEPT
$IPT -A udp_inbound -p UDP -s 0/0 --destination-port 27007 -j ACCEPT
$IPT -A udp_inbound -p UDP -s 0/0 --destination-port 27015 -j ACCEPT
$IPT -A udp_inbound -p UDP -s 0/0 --destination-port 27025 -j ACCEPT
$IPT -A udp_inbound -p UDP -s 0/0 --destination-port 137 -j DROP
$IPT -A udp_inbound -p UDP -s 0/0 --destination-port 138 -j DROP
$IPT -A udp_inbound -p UDP -s 0/0 --destination-port 123 -j ACCEPT
$IPT -A udp_inbound -p UDP -s 0/0 --destination-port 53 -j ACCEPT
$IPT -A udp_inbound -p UDP -s 0/0 --source-port 67 --destination-port 68 -j ACCEPT
$IPT -A udp_inbound -p UDP -j RETURN

$IPT -A udp_outbound -p UDP -s 0/0 -j ACCEPT

$IPT -A tcp_inbound -p TCP -s 0/0 --destination-port 80 -j ACCEPT
$IPT -A tcp_inbound -p TCP -s 0/0 --destination-port 443 -j ACCEPT
$IPT -A tcp_inbound -p TCP -s 0/0 --destination-port 21 -j ACCEPT
$IPT -A tcp_inbound -p TCP -s 0/0 --source-port 20 -j ACCEPT
$IPT -A tcp_inbound -p TCP -s 0/0 --destination-port 25 -j ACCEPT
$IPT -A tcp_inbound -p TCP -s 0/0 --destination-port 110 -j ACCEPT
$IPT -A tcp_inbound -p TCP -s 0/0 --destination-port 22 -j ACCEPT
$IPT -A tcp_inbound -p TCP -j RETURN

$IPT -A tcp_outbound -p TCP -s 0/0 -j ACCEPT

echo "Processing INPUT chain ..."

$IPT -A INPUT -p ALL -i $LO_IFACE -j ACCEPT
$IPT -A INPUT -p ALL -j bad_packets
$IPT -A INPUT -p ALL -i $LOCAL_IFACE -s $LOCAL_NET -j ACCEPT
$IPT -A INPUT -p ALL -i $LOCAL_IFACE -d $LOCAL_BCAST -j ACCEPT
$IPT -A INPUT -p ALL -i $INET_IFACE -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A INPUT -p TCP -i $INET_IFACE -j tcp_inbound
$IPT -A INPUT -p UDP -i $INET_IFACE -j udp_inbound
$IPT -A INPUT -p ICMP -i $INET_IFACE -j icmp_packets

$IPT -A INPUT -p ALL -d 255.255.255.255 -j DROP

$IPT -A INPUT -m limit --limit 3/minute --limit-burst 3 -j LOG --log-prefix "INPUT packet died: "

echo "Processing FORWARD chain ..."

$IPT -A FORWARD -p ALL -j bad_packets
$IPT -A FORWARD -p tcp -i $LOCAL_IFACE -j tcp_outbound
$IPT -A FORWARD -p udp -i $LOCAL_IFACE -j udp_outbound
$IPT -A FORWARD -p ALL -i $LOCAL_IFACE -j ACCEPT
$IPT -A FORWARD -i $INET_IFACE -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -m limit --limit 3/minute --limit-burst 3 -j LOG --log-prefix "FORWARD packet died: "

echo "Processing OUTPUT chain ..."

$IPT -A OUTPUT -m state -p icmp --state INVALID -j DROP
$IPT -A OUTPUT -p ALL -s $LO_IP -j ACCEPT
$IPT -A OUTPUT -p ALL -o $LO_IFACE -j ACCEPT
$IPT -A OUTPUT -p ALL -s $LOCAL_IP -j ACCEPT
$IPT -A OUTPUT -p ALL -o $LOCAL_IFACE -j ACCEPT
$IPT -A OUTPUT -p ALL -o $INET_IFACE -j ACCEPT
$IPT -A OUTPUT -m limit --limit 3/minute --limit-burst 3 -j LOG --log-prefix "OUTPUT csomag meghalt: "

echo "Setting up NAT/Masquerading ..."

$IPT -t nat -A POSTROUTING -o $INET_IFACE -j MASQUERADE

###

Abraham Gyorgy
Hungary

---

