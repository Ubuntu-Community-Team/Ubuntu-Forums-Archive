---
title: "Monitor and manage bandwidth usage on Ubuntu Server gateway"
date: 2014-03-07
forum: Networking &amp; Wireless
---

### Post by massimo.cristofoli on 2014-03-07
Hi everyone,

I have a system with Ubuntu Server 12.04 that works as a gatway for the LAN. Here is the configuration
```
[MODEM]---<eth0>[UBUNTU SERVER]<eth1 (IP: 10.0.10.1)>---[LAN PCs (IP: 10.0.10.XXX)]
```
The server works as firewall (iptables), DHCP and few more services.

I have some bandwidth problems when using some external services, e.g. WeTransfer (with large files). What happens is that the internet connection becomes hardly usable by all users.
Our internet provider says that the upload bandwidth reaches the limit.
Monitoring the bandwidth on both eth0 and eth1 with tcptrack ($> tcktrack -i eth1) it doesn't seems that the pc using wetrasfer is using that much bandwidth; tcptrack displays around 100 KB/s, with a total of 150 KB/s for all the LAN.
Question 1: is it tcptrack reliable to monitor traffic from/to LAN? Am I using it wrong?

I would like to limit the bandwidth of the single LAN machines to a given value, so each machine can download at max 1MB/s and upload at max 100KB/s (I will tune these parameters after testing). I've read something about "tc", but didn't find how to let it work correctly. The first test I made is to limit bandwidth of a single PC, and upload something to WeTransfer with this PC. It looks like the bandwidth wasn't limited (from tcptrack reading and the bandwidth problem experienced by all the LAN). Here is the script I used to limit the bandwidth (found here: [http://www.iplocation.net/tools/traffic-control.php](http://www.iplocation.net/tools/traffic-control.php) Changed interface, IP and limits)

```
#!/bin/bash
#
#  tc uses the following units when passed as a parameter.
#  kbps: Kilobytes per second
#  mbps: Megabytes per second
#  kbit: Kilobits per second
#  mbit: Megabits per second
#  bps: Bytes per second
#       Amounts of data can be specified in:
#       kb or k: Kilobytes
#       mb or m: Megabytes
#       mbit: Megabits
#       kbit: Kilobits
#  To get the byte figure from bits, divide the number by 8 bit
#

#
# Name of the traffic control command.
TC=/sbin/tc

# The network interface we're planning on limiting bandwidth.
IF=eth1             # Interface

# Download limit (in mega bytes)
DNLD=10kbit         # DOWNLOAD Limit

# Upload limit (in kilo bytes)
UPLD=10kbit          # UPLOAD Limit

# IP address of the machine we are controlling
IP=10.0.10.100     # Host IP

# Filter options for limiting the intended interface.
U32="$TC filter add dev $IF protocol ip parent 1:0 prio 1 u32"

start() {

# We'll use Hierarchical Token Bucket (HTB) to shape bandwidth.
# For detailed configuration options, please consult Linux man
# page.

$TC qdisc add dev $IF root handle 1: htb default 30
$TC class add dev $IF parent 1: classid 1:1 htb rate $DNLD
$TC class add dev $IF parent 1: classid 1:2 htb rate $UPLD
$U32 match ip dst $IP/32 flowid 1:1
$U32 match ip src $IP/32 flowid 1:2

# The first line creates the root qdisc, and the next two lines
# create two child qdisc that are to be used to shape download
# and upload bandwidth.
#
# The 4th and 5th line creates the filter to match the interface.
# The 'dst' IP address is used to limit download speed, and the
# 'src' IP address is used to limit upload speed.

}

stop() {

# Stop the bandwidth shaping.
$TC qdisc del dev $IF root

}

restart() {

# Self-explanatory.
stop
sleep 1
start

}

show() {

# Display status of traffic control status.
$TC -s qdisc ls dev $IF

}

case "$1" in

start)

echo -n "Starting bandwidth shaping: "
start
echo "done"
;;

stop)

echo -n "Stopping bandwidth shaping: "
stop
echo "done"
;;

restart)

echo -n "Restarting bandwidth shaping: "
restart
echo "done"
;;

show)

echo "Bandwidth shaping status for $IF:"
show
echo ""
;;

*)

pwd=$(pwd)
echo "Usage: tc.bash {start|stop|restart|show}"
;;

esac

exit 0
```

Question 2: how to let it work correctly? What could be the problem?
First, I need to let it work for a single IP, or for all the interface connections.
Than, as said, I need to set a limit for EACH LAN device. Setting a global limit is probably not a good choice, since a WeTransfer user will use all the bandwith till the limit, and other users have, again, problem using the internet connection.
Maybe there is a simpler approach, using e.g. squid proxy or other services. Hints?

Thanks!
MIX

---

