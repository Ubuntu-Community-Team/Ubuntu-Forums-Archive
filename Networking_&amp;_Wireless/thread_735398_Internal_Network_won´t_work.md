---
title: "Internal Network won´t work"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by nzquiet1 on 2008-03-25
Greetings All, after trying several suggestions found from the site and archives, I´ve now managed to stop my internal network from working correctly, so am now completely stumped.

**Issue I had:**
originally was slow internet, which the answer seemed to be to disable IPv6, but the changes didn´t work for me, so went to plan B, and purchased a new network card.

**Situation I have now:**
Main server, build in network plus Realtek 8169 PCI card, running Ubuntu of course :-). Original network card was a realtek 8139..
Both network cards work fine, as in I can surf the internet which I switch them around (ie eth0 to eth1) via the /etc/udev/rules.d/70-persistent-net-rules file  except the internal network is not working as I can´t ping or http through or connect to any of the internal machines.  I have tried leaving the firewall wideopen, and still no change.

So I want to get my internal network talking to the server so that it will allow for the internals to hit the internet.

Some details that may help are below

Appreciate any assistance or guideance anyone can give as my eyes haven´t as yet figured out the problem.

Regards, 
  NzQuiet1

lshw:```

root@gateway:/etc/udev/rules.d# lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth1
       version: 10
       serial: 00:08:54:53:29:7b
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=203.97.101.222 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:15:f2:c4:65:89
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.20.1 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
```

lspci:
```
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
```

interfaces file:
```
root@gateway:/etc/udev/rules.d# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The Primary internal network
auto eth0
iface eth0 inet static
        address 192.168.20.1
        netmask 255.255.255.0
        network 192.168.20.0
        broadcast 192.168.20.255
        gateway 192.168.20.1

# The Primary EXTERNAL connection (Internet)
auto eth1
iface eth1 inet static
        address 203.97.101.222
        netmask 255.255.255.0
        gateway 203.97.101.1

```

ifconfig:
```
root@gateway:/etc/udev/rules.d# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:F2:C4:65:89  
          inet addr:192.168.20.1  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fec4:6589/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:14
          TX packets:361 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:678 (678.0 b)  TX bytes:30401 (29.6 KB)
          Interrupt:19 Base address:0xa800 

eth1      Link encap:Ethernet  HWaddr 00:08:54:53:29:7B  
          inet addr:203.97.101.222  Bcast:203.97.101.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fe53:297b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27653014 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67043 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1673168974 (1.5 GB)  TX bytes:12787101 (12.1 MB)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:388579 (379.4 KB)  TX bytes:388579 (379.4 KB)

```

and finally the firewall script:
```
root@gateway:/etc/udev/rules.d# cat /etc/init.d/rc.firewall
#!/bin/sh 
#
#  This is automatically generated file. DO NOT MODIFY !
#
#  Firewall Builder  fwb_ipt v2.1.14-1 
#
#  Generated Sun Mar 23 21:52:40 2008 NZDT by nzquiet1
#
# files: * Ohkiwi.fw
#
#
#  
#
#
#


PATH="/sbin:/usr/sbin:/bin:/usr/bin:${PATH}"
export PATH

LSMOD="/sbin/lsmod"
MODPROBE="/sbin/modprobe"
IPTABLES="/sbin/iptables"
IPTABLES_RESTORE="/sbin/iptables-restore"
IP="/sbin/ip"
LOGGER="/bin/logger"


#
# Prolog script
#

#
# End of prolog script
#

log() {
  echo "$1"
  test -x "$LOGGER" && $LOGGER -p info "$1"
}

check_file() {
  test -r "$2" || {
    echo "Can not find file $2 referenced by AddressTable object $1"
    exit 1
  }
}

va_num=1
add_addr() {
  addr=$1
  nm=$2
  dev=$3

  type=""
  aadd=""

  L=`$IP -4 link ls $dev | head -n1`
  if test -n "$L"; then
    OIFS=$IFS
    IFS=" /:,<"
    set $L
    type=$4
    IFS=$OIFS
    if test "$type" = "NO-CARRIER"; then
      type=$5
    fi

    L=`$IP -4 addr ls $dev to $addr | grep inet | grep -v :`
    if test -n "$L"; then
      OIFS=$IFS
      IFS=" /"
      set $L
      aadd=$2
      IFS=$OIFS
    fi
  fi
  if test -z "$aadd"; then
    if test "$type" = "POINTOPOINT"; then
      $IP -4 addr add $addr dev $dev scope global label $dev:FWB${va_num}
      va_num=`expr $va_num + 1`
    fi
    if test "$type" = "BROADCAST"; then
      $IP -4 addr add $addr/$nm dev $dev brd + scope global label $dev:FWB${va_num}
      va_num=`expr $va_num + 1`
    fi
  fi
}

getInterfaceVarName() {
  echo $1 | sed 's/\./_/'
}

getaddr() {
  dev=$1
  name=$2
  L=`$IP -4 addr show dev $dev | grep inet | grep -v :`
  test -z "$L" && { 
    eval "$name=''"
    return
  }
  OIFS=$IFS
  IFS=" /"
  set $L
  eval "$name=$2"
  IFS=$OIFS
}


getinterfaces() {
  NAME=$1
  $IP link show | grep ": $NAME" | while read L; do
    OIFS=$IFS
    IFS=" :"
    set $L
    IFS=$OIFS
    echo $2
  done
}


# increment ip address
incaddr()
{
  n1=$4
  n2=$3
  n3=$2
  n4=$1

  vn1=`eval  "echo \\$$n1"`

  R=`expr $vn1 \< 255`
  if test $R = "1"; then
    eval "$n1=`expr $vn1 + 1`"
  else
    eval "$n1=0"
    incaddr XX $n4 $n3 $n2
  fi
}

if $IP link ls >/dev/null 2>&1; then
  echo;
else
  echo "iproute not found"
  exit 1
fi



MODULES_DIR="/lib/modules/`uname -r`/kernel/net/"
MODULES=`find $MODULES_DIR -name '*conntrack*'|sed  -e 's/^.*\///' -e 's/\([^\.]\)\..*/\1/'`
MODULES="$MODULES `find $MODULES_DIR -name '*nat*'|sed  -e 's/^.*\///' -e 's/\([^\.]\)\..*/\1/'`"
for module in $MODULES; do 
  if $LSMOD | grep ${module} >/dev/null; then continue; fi
  $MODPROBE ${module} ||  exit 1 
done


# Using 0 address table files


INTERFACES="eth0 eth1 lo "
for i in $INTERFACES ; do
  $IP link show "$i" > /dev/null 2>&1 || {
    log "Interface $i does not exist"
    exit 1
  }
done


# Configure interfaces
$IP -4 neigh flush dev eth0 >/dev/null 2>&1
$IP -4 addr flush dev eth0 secondary label "eth0:FWB*" >/dev/null 2>&1
$IP -4 neigh flush dev eth1 >/dev/null 2>&1
$IP -4 addr flush dev eth1 secondary label "eth1:FWB*" >/dev/null 2>&1


add_addr 192.168.20.1 24 eth0
$IP link set eth0 up
add_addr 203.97.101.222 24 eth1
$IP link set eth1 up
add_addr 127.0.0.1 24 lo
$IP link set lo up


# Add virtual addresses for NAT rules


log 'Activating firewall script generated Sun Mar 23 21:52:40 2008  by nzquiet1'

$IPTABLES -P OUTPUT  DROP
$IPTABLES -P INPUT   DROP
$IPTABLES -P FORWARD DROP


cat /proc/net/ip_tables_names | while read table; do
  $IPTABLES -t $table -L -n | while read c chain rest; do
      if test "X$c" = "XChain" ; then
        $IPTABLES -t $table -F $chain
      fi
  done
  $IPTABLES -t $table -X
done


$IPTABLES -A INPUT   -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A OUTPUT  -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

# 
# Rule 0 (NAT)
# 
echo "Rule 0 (NAT)"
# 
# 
$IPTABLES -t nat -A POSTROUTING -o eth1  -s 192.168.20.0/24 -j SNAT --to-source 203.97.101.222 
# 
# Rule 0 (eth1)
# 
echo "Rule 0 (eth1)"
# 
# Anti Spoof Rule
# 
$IPTABLES -N In_RULE_0
$IPTABLES -A INPUT  -i eth1  -s 192.168.20.1  -j In_RULE_0 
$IPTABLES -A INPUT  -i eth1  -s 203.97.101.222  -j In_RULE_0 
$IPTABLES -A INPUT  -i eth1  -s 192.168.20.0/24  -j In_RULE_0 
$IPTABLES -A FORWARD  -i eth1  -s 192.168.20.1  -j In_RULE_0 
$IPTABLES -A FORWARD  -i eth1  -s 203.97.101.222  -j In_RULE_0 
$IPTABLES -A FORWARD  -i eth1  -s 192.168.20.0/24  -j In_RULE_0 
$IPTABLES -A In_RULE_0  -j LOG  --log-level info --log-prefix "Spoof"
$IPTABLES -A In_RULE_0  -j DROP 
# 
# Rule 1 (lo)
# 
echo "Rule 1 (lo)"
# 
# Allow everything on loopback
# 
$IPTABLES -A INPUT  -i lo  -m state --state NEW  -j ACCEPT 
$IPTABLES -A OUTPUT  -o lo  -m state --state NEW  -j ACCEPT 
# 
# Rule 2 (eth0)
# 
echo "Rule 2 (eth0)"
# 
# Any access from inside LAN only is allowed to the FW
# 
$IPTABLES -A INPUT  -i eth0  -s 192.168.20.0/24  -m state --state NEW  -j ACCEPT 
$IPTABLES -N Cid474F8CE95849.0
$IPTABLES -A OUTPUT  -o eth0  -s 192.168.20.0/24  -m state --state NEW  -j Cid474F8CE95849.0 
$IPTABLES -A Cid474F8CE95849.0  -d 192.168.20.1  -j ACCEPT 
$IPTABLES -A Cid474F8CE95849.0  -d 203.97.101.222  -j ACCEPT 
$IPTABLES -N Cid474F8CE95849.1
$IPTABLES -A FORWARD  -o eth0  -s 192.168.20.0/24  -m state --state NEW  -j Cid474F8CE95849.1 
$IPTABLES -A Cid474F8CE95849.1  -d 192.168.20.1  -j ACCEPT 
$IPTABLES -A Cid474F8CE95849.1  -d 203.97.101.222  -j ACCEPT 
# 
# Rule 3 (global)
# 
echo "Rule 3 (global)"
# 
# Allow access to HTTP
# 
$IPTABLES -N Cid474F8D7C5849.0
$IPTABLES -A OUTPUT -p tcp -m tcp  -m multiport  --dports 80,443  -m state --state NEW  -j Cid474F8D7C5849.0 
$IPTABLES -A Cid474F8D7C5849.0  -d 192.168.20.1  -j ACCEPT 
$IPTABLES -A Cid474F8D7C5849.0  -d 203.97.101.222  -j ACCEPT 
$IPTABLES -A INPUT -p tcp -m tcp  -m multiport  --dports 80,443  -m state --state NEW  -j ACCEPT 
# 
# Rule 4 (global)
# 
echo "Rule 4 (global)"
# 
# Allow access to SSH
# 
$IPTABLES -N Cid47532D8F5088.0
$IPTABLES -A OUTPUT -p tcp -m tcp  --dport 22  -m state --state NEW  -j Cid47532D8F5088.0 
$IPTABLES -A Cid47532D8F5088.0  -d 192.168.20.1  -j ACCEPT 
$IPTABLES -A Cid47532D8F5088.0  -d 203.97.101.222  -j ACCEPT 
$IPTABLES -A INPUT -p tcp -m tcp  --dport 22  -m state --state NEW  -j ACCEPT 
# 
# Rule 5 (global)
# 
echo "Rule 5 (global)"
# 
# Allow access to ISPConfig from external
# 
$IPTABLES -N Cid476B8E264997.0
$IPTABLES -A OUTPUT -p tcp -m tcp  --dport 81  -m state --state NEW  -j Cid476B8E264997.0 
$IPTABLES -A Cid476B8E264997.0  -d 192.168.20.1  -j ACCEPT 
$IPTABLES -A Cid476B8E264997.0  -d 203.97.101.222  -j ACCEPT 
$IPTABLES -A INPUT -p tcp -m tcp  --dport 81  -m state --state NEW  -j ACCEPT 
# 
# Rule 6 (global)
# 
echo "Rule 6 (global)"
# 
# Allow access to FTP
# 
$IPTABLES -N Cid47532D9D5088.0
$IPTABLES -A OUTPUT -p tcp -m tcp  --sport 20  --dport 1024:65535  -m state --state NEW  -j Cid47532D9D5088.0 
$IPTABLES -A OUTPUT -p tcp -m tcp  -m multiport  --dports 21,20  -m state --state NEW  -j Cid47532D9D5088.0 
$IPTABLES -A Cid47532D9D5088.0  -d 192.168.20.1  -j ACCEPT 
$IPTABLES -A Cid47532D9D5088.0  -d 203.97.101.222  -j ACCEPT 
$IPTABLES -A INPUT -p tcp -m tcp  --sport 20  --dport 1024:65535  -m state --state NEW  -j ACCEPT 
$IPTABLES -A INPUT -p tcp -m tcp  -m multiport  --dports 21,20  -m state --state NEW  -j ACCEPT 
# 
# Rule 7 (global)
# 
echo "Rule 7 (global)"
# 
# Allow DNS queries
# 
$IPTABLES -N Cid474F8D905849.0
$IPTABLES -A OUTPUT -p tcp -m tcp  --dport 53  -m state --state NEW  -j Cid474F8D905849.0 
$IPTABLES -A OUTPUT -p udp -m udp  --dport 53  -m state --state NEW  -j Cid474F8D905849.0 
$IPTABLES -A Cid474F8D905849.0  -d 192.168.20.1  -j ACCEPT 
$IPTABLES -A Cid474F8D905849.0  -d 203.97.101.222  -j ACCEPT 
$IPTABLES -A INPUT -p tcp -m tcp  --dport 53  -m state --state NEW  -j ACCEPT 
$IPTABLES -A INPUT -p udp -m udp  --dport 53  -m state --state NEW  -j ACCEPT 
# 
# Rule 8 (global)
# 
echo "Rule 8 (global)"
# 
# FW allowed anywhere
# 
$IPTABLES -A INPUT  -s 192.168.20.1  -m state --state NEW  -j ACCEPT 
$IPTABLES -A INPUT  -s 203.97.101.222  -m state --state NEW  -j ACCEPT 
$IPTABLES -A OUTPUT  -m state --state NEW  -j ACCEPT 
# 
# Rule 9 (global)
# 
echo "Rule 9 (global)"
# 
# 'masquerading' rule
# 
$IPTABLES -A INPUT  -s 192.168.20.0/24  -m state --state NEW  -j ACCEPT 
$IPTABLES -A OUTPUT  -s 192.168.20.0/24  -m state --state NEW  -j ACCEPT 
$IPTABLES -A FORWARD  -s 192.168.20.0/24  -m state --state NEW  -j ACCEPT 
# 
# Rule 10 (global)
# 
echo "Rule 10 (global)"
# 
# "catch all" rule
# 
$IPTABLES -N RULE_10
$IPTABLES -A OUTPUT  -j RULE_10 
$IPTABLES -A INPUT  -j RULE_10 
$IPTABLES -A FORWARD  -j RULE_10 
$IPTABLES -A RULE_10  -j LOG  --log-level info --log-prefix "RULE 10 -- DENY "
$IPTABLES -A RULE_10  -j DROP 
#
#
echo 1 > /proc/sys/net/ipv4/ip_forward


#
# Epilog script
#


# End of epilog script
#

```

---

### Post by Iowan on 2008-03-25
The gateway statement on eth0 doesn't seem right...

---

### Post by nzquiet1 on 2008-03-25
tried commenting it out, but no difference :-(.  But in saying that I can´t ping from server or to server, although I can do this from the internet, ie I can ping google, and I can ping into my system as well.

---

### Post by Iowan on 2008-03-25
Check the routing table...

Am I missing the VT-6102 card in **lspci?** I don't see it...

---

### Post by nzquiet1 on 2008-03-25
> **Iowan said:**
> Check the routing table...

Am I missing the VT-6102 card in **lspci?** I don't see it...

It&#347; there, just didn´t include it:

```
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration

```

And Routing table currently is:
```
root@gateway:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.20.0    *               255.255.255.0   U     0      0        0 eth0
203.97.101.0    *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         203-97-101-1.ca 0.0.0.0         UG    100    0        0 eth1

```

---

### Post by Iowan on 2008-03-25
> **nzquiet1 said:**
> ...
And Routing table currently is:
```
root@gateway:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.20.0    *               255.255.255.0   U     0      0        0 eth0
203.97.101.0    *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         [COLOR="Red"]203-97-101-1.ca[/COLOR] 0.0.0.0         UG    100    0        0 eth1

```Somehow this doesn't look kosher, either - but my batting average isn't too good right now...
Can you turn the firewall completely OFF?

---

### Post by nzquiet1 on 2008-03-25
dropping all the firewall rules, didn´t seem to make a difference either way.  Still comes up distination unreachable on the internal network :-(

---

### Post by nzquiet1 on 2008-03-26
bump - still not having much luck, any suggestions that I could try out there please ??

---

### Post by nzquiet1 on 2008-03-29
managed to sort out the problem, although have no idea why it has fixed it.  Seemed that the issue was the switch I was using, when I changed to use the other one I have, the system all worked correctly.   Very weird.

---

