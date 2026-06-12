---
title: "Route Problem for 2 External Provider"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by smadon on 2008-08-13
Hi,

I have 2 internet providers on 2 network card, but from outside, if i do a traceroute, sometime the second public ip (configure on the first network card eth0) reply on the second network card (eth2). How can I stop that ?
My configuration
Provider 1 (ADSL.....) ----- Eth2 |...My....|
Provider 2 (203.x.x.6) ----- Eth1 |.Server..|--Eth0 - LAN

My script :

```

#######################################################
##    Configuration for several Internet Connection  ##
#######################################################
## Check :  http://lartc.org/howto/lartc.rpdb.multiple-links.html

echo "[Configuration for Mutiple Provider]"
# Connection 1 :
IF1="eth0"
IP1="203.X.X.6"
P1_GW="203.X.X.5"
P1_NET="203.X.X.5/29"

# Connection 2 : ADSL
IF2="eth2"
IP2="10.0.1.2"
P2_GW="10.0.1.1"
P2_NET="10.0.1.0/24"

# Local Network
IF0="eth1"
IP0="10.0.0.1"
P0_GW="10.0.0.2"
P0_NET="10.0.0.0/24"

# Table
T1="201"
T2="202"

# Data for Backup
IP_Server="192.68.2.0/24"

echo "Resume For Information on the Config on the different Network: "
echo "Astinet : Port=" $IF1 ", IP=" $IP1 ", Network=" $P1_NET ", IP Gateway=" $P1_GW
echo "Speedy  : Port=" $IF2 ", IP=" $IP2 ", Network=" $P2_NET ", IP Gateway=" $P2_GW
echo "LAN     : Port=" $IF0 ", IP=" $IP0 ", Network=" $P0_NET ", IP Gateway=" $P0_GW

# Flush all Route
echo "Flushing Old Routes"
#ip route flush all
ip route flush cache
ip route flush table $T1
ip route flush table $T2
#ip rule flush

# Create Routing tables for eache Provider
echo "Creating Default Routing Table"
ip route add $P1_NET dev $IF1   src $IP1 table $T1
ip route add default via $P1_GW          table $T1
ip route add $P2_NET dev $IF2   src $IP2 table $T2
ip route add default via $P2_GW          table $T2

# Create Main Route
echo "Creating Main Route"
ip route add $P1_NET dev $IF1 src $IP1
ip route add $P2_NET dev $IF2 src $IP2
ip route add $P0_NET dev $IF0 src $IP0

# Set Routing Rules
echo "Creating Routing Rules"
ip rule add from $IP1 table $T1
ip rule add from $IP2 table $T2
ip route add $P0_NET     dev $IF0 table $T1
ip route add $P2_NET     dev $IF2 table $T1
ip route add 127.0.0.0/8 dev lo   table $T1
ip route add $P0_NET     dev $IF0 table $T2
ip route add $P1_NET     dev $IF1 table $T2
ip route add 127.0.0.0/8 dev lo   table $T2

echo "Add Server Route"
#ip route add $IP_Server dev $IF0 table $T2
#ip route add $IP_Server dev $IF0 table $T1

# Define routing rule for marked packages
echo "Mark Routing"
ip rule add fwmark 1 table $T1

# Creating the Load Balancing
ip route add default scope global nexthop via $P1_GW dev $IF1 weight 1 nexthop via $P2_GW dev $IF2 weight 3
 

```

So, How can I stop traffic from eth2 to eth0 and reverse.

Thanks for your help
Smad :-)

---

