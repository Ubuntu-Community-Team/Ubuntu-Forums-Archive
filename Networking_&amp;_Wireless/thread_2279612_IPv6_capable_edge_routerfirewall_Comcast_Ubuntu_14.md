---
title: "IPv6 capable edge router/firewall Comcast Ubuntu 14.04"
date: 2015-05-24
forum: Networking &amp; Wireless
---

### Post by BatteryKing on 2015-05-24
(Updating this post because I finally got around to setting up multiple VLANs and learned a few things along the way.  If you are not using multiple VLANs, it is mainly just extra information, so...)
I scratch built a router out of a mini-ITX box I had laying around as I lack faith in my Netgear wireless router because Netgear can never release a patch for it that works and the firmware is getting very old on it now.  Also I had a mini-ITX system just sitting around collecting dust that seemed like a good candidate to turn into a router / firewall.

I am curious on how correct I got this thing and also thought somebody might be interested in a little consolidated howto as I pulled information from all over the Internet in order to get this going.  So below is what I basically did (sans a lot of mistakes I made along the way as that would definitely take up too much space):

I. Configuring a null serial terminal:
1. Picked up a USB to null serial cable.  (The mini-ITX board has an RS-232 port built in.)

2. Go to serial console howto: [https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)

3. `su -`

4. `cd /etc/init`

5. Add serial console while kernel is running `vim ttyS0.conf`

6. append "respawn
               exec /sbin/getty -L 115200 ttyS0 vt102"

7. `start ttyS0`

8. Add grub configuration - Made /etc/default/grub look like this:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX="console=tty0 console=ttyS0,115200n8"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console
GRUB_TERMINAL=serial
GRUB_SERIAL_COMMAND="serial --speed=115200 --unit=0 --word=8 --parity=no --stop=1"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

9. `update-grub`

10. Remove window manager (could also install server):
   a. `update-rc.d -f gdm remove`
   b. `echo "manual" >> /etc/init/lightdm.override`

11. Install minicom on controlling computer.  For my USB device it comes up as /dev/ttyUSB0

12. Set minicom speed to 115200 8N1

13. When minicom is ready, reboot and see if serial console comes up.  Should be able to see starting at grub and then the boot sequence as the OS boots through minicom.


II. Install ssh server.  (Use serial console only when networking is down and to monitor boot process.  Kind of quirky for other tasks.)
1. `apt-get install ssh`
2. I don't know about some people, but if you are not going to enable direct Internet access, which I don't, then it does get tempting to enable root logins.  (Root login needs to be explicitly enabled.)

III. I installed a UPS monitoring client as my APC UPS has its USB port plugged into a different machine, but both machines are connected to the UPS.  Linux makes it free and easy to share a UPS between multiple machines.

IV. Added WLAN device so I could connect to my phone's hotspot in case Comcast goes down.  (I knew there was a reason why I went the extra mile to keep my unlimited Verizon plan.)
1. Install gui network manager (sorry, couldn't get it to work any other way) - `apt-get install network-manager`
2. Fire up gui based connection editor (through ssh -X root connection): `nm-connection-editor`
3. Add entry for WiFi network in gui, save, and quit.
4. Command for starting WiFi connection: `nmcli c up id <my hotspot>`
5. Command for stopping WiFi connection: `nmcli c down id <my hotspot>`
6. Probably want to put these commands into script files for easy access.

IV b. VLAN networking
1. `apt-get install vlan`
2. `modprobe 8021q`
3. Edit /detc/modules and add 8021q module.
4. `vconfig add eth<x> <a>`
5. Edit /etc/network/interfaces:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo eth0 eth1 eth<x>.<a> eth<x>.<b>
iface lo inet loopback

iface eth<x> inet static
        address 192.168.<x>.<a>
        netmask 255.255.255.0

iface eth<x>.<a> inet static
    address 192.168.<x>.<a>
    netmask 255.255.255.0
        vlan-raw-device eth0

iface eth<x>.<b> inet static
    address 192.168.<y>.<a>
    netmask 255.255.255.0
        vlan-raw-device eth0

iface eth1 inet dhcp

```

V. Setting up forwarding / firewalling rules and packet prioritization.
1. I made a big script file to get the job done (adapted from: [http://www.linuxhelp.net/guides/iptables/):](http://www.linuxhelp.net/guides/iptables/):)
```

#!/bin/bash -x
# 
# In order to use this IPTables firewall script you
# must have IPTables installed. You also must be using 
# a 2.4.x series Kernel, with IPTables support complied 
# into it, which is standard for most newer Linux distributions.
#
# If you need help compiling IPtables into your kernel, please
# see our Kernel Compile/Upgrade Guide located at 
# [www.linuxhelp.net/guides/](www.linuxhelp.net/guides/)
#
# Once the script has been edited with all your relevant
# information (IP's, Network Interfaces, etc..) simply
# make the script executable and run it as root.
#
# chmod 700 iptables-firewall
# ./iptables-firewall
#
# If you would like to see what rules are currently set, as
# root run iptables -L
#
# If you've messed up and need to bring down the firewall 
# for whatever reason, run iptables -F
#
# If you would like to have the firewall automatically
# come up at boot time, add the path to the script to
# the bottom of your /etc/rc.d/rc.local file. For instance
# /root/bin/iptables-firewall
#
# If you're not sure about something, check out the iptables
# man page by typing 'man iptables' (without the ''s) at the
# command prompt.
#
# This script is an enhanced/modified version of the 
# iptables-script written by Davion 
# 
# If you have any questions, please come see us in #Linuxhelp.net
# on the DALnet IRC network. ([www.linuxhelp.net/ircinfo.shtml](www.linuxhelp.net/ircinfo.shtml))

# The location of the IPtables binary file on your system.
IPT="/sbin/iptables"
IPT6="/sbin/ip6tables"
<internal machine name with services open>="192.168.x.x"
<internal machine name with services open>v6="<current Internet accessible address with MAC address based IP>"

# The Network Interface you will be protecting. For ADSL/dialup users,
# ppp0 should be fine. If you are using a cable internet connection or
# are connected to a LAN, you will have to change this to "eth0".
WAN="eth<y>"
LAN="eth<x>"
DMZ="eth<x>.<a>"
UNT="eth<x>.<b>" #Untrusted Network

LAN_PREFIX="192.168.<a>"
DMZ_PREFIX="192.168.<b>"
UNT_PREFIX="192.168.<c>"

LAN6_PREFIX="1234:1234:1234:123a"
DMZ6_PREFIX="1234:1234:1234:123b"
UNT6_PREFIX="1234:1234:1234:123c"

LAN_NET="$LAN_PREFIX.0/24"
DMZ_NET="$DMZ_PREFIX.0/24"
UNT_NET="$UNT_PREFIX.0/24"

LAN6_NET="$LAN6_PREFIX::/64"
DMZ6_NET="$DMZ6_PREFIX::/64"
UNT6_NET="$UNT6_PREFIX::/64"

#Nodes route to
MACHINEX="$LAN_PREFIX.<x>"
MACHINEXv6="$LAN6_PREFIX:<static 64 bits>"
MACHINEY="$DMZ_PREFIX.<y>"
MACHINEYv6="$DMZ6_PREFIX:<static 64 bits>"

# The following rules will clear out any existing firewall rules, 
# and any chains that might have been created.
$IPT -F
$IPT -F INPUT
$IPT -F OUTPUT
$IPT -F FORWARD
$IPT -F -t nat
$IPT -X
# IPv6
$IPT6 -F
$IPT6 -X

# These will setup our policies.
$IPT -P INPUT DROP
$IPT -P OUTPUT ACCEPT
$IPT -P FORWARD ACCEPT
# IPv6
$IPT6 -P INPUT DROP
$IPT6 -P OUTPUT ACCEPT
$IPT6 -P FORWARD DROP

# The following line below enables IP forwarding and thus 
# by extension, NAT. Turn this on if you're going to be 
# doing NAT or IP Masquerading.
echo 1 > /proc/sys/net/ipv4/ip_forward

# Enable IPv6 routing advertisements and forwarding for IPv6 routing.
sysctl net.ipv6.conf.eth1.accept_ra=2
sysctl net.ipv6.conf.all.forwarding=1

#Deny DMZ to Internal
$IPT -A FORWARD -s $DMZ_NET -d $LAN_NET -m state --state NEW -j REJECT -m comment --comment "Deny DMZ access to Internal"
$IPT6 -A FORWARD -s $DMZ6_NET -d $LAN6_NET -m state --state NEW -j REJECT -m comment --comment "Deny DMZ access to Internal"

#Deny UNT to Internal
$IPT -A FORWARD -s $UNT_NET -d $LAN_NET -j REJECT -m comment --comment "Deny UNT access to Internal"
$IPT -A FORWARD -s $UNT_NET -d $DMZ_NET -j REJECT -m comment --comment "Deny UNT access to DMZ"
$IPT6 -A FORWARD -s $UNT6_NET -d $LAN6_NET -j REJECT -m comment --comment "Deny UNT access to Internal"
$IPT6 -A FORWARD -s $UNT6_NET -d $DMZ6_NET -j REJECT -m comment --comment "Deny UNT access to DMZ"

# Allow IPv6 ICMP to pass.
$IPT6 -A INPUT -p icmpv6 -j ACCEPT
$IPT6 -A OUTPUT -p icmpv6 -j ACCEPT
$IPT6 -A FORWARD -p icmpv6 -j ACCEPT

# Source NAT everything heading out the $WAN (external) 
# interface to be the given IP. If you have a dynamic IP 
# address or a DHCP IP that changes semi-regularly, comment out 
# the first line and uncomment the second line.
#
# Remember to change the ip address below to your static ip.
#
$IPT -t nat -A POSTROUTING -o $WAN -j MASQUERADE

# For IPv6 as no NAT, allow full outgoing connection, (but no incomming by default).
$IPT6 -A INPUT -i $WAN -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT6 -A INPUT -i $LAN -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT6 -A INPUT -i $DMZ -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT6 -A INPUT -i $UNT -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT6 -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
$IPT6 -A FORWARD -i $LAN -m state --state NEW -j ACCEPT
$IPT6 -A FORWARD -i $DMZ -m state --state NEW -j ACCEPT
$IPT6 -A FORWARD -i $UNT -m state --state NEW -j ACCEPT

# This rule protects your fowarding rule(s).
#$IPT -A FORWARD -i $WAN -m state --state NEW,INVALID -j DROP

# If you would like to forward specific ports to other machines
# on your home network, edit and uncomment the rules below.
$IPT -t nat -A PREROUTING -i $WAN -p tcp --dport <internet port> -j DNAT --to $<internal machine>:22             #SSH <internal machine>
$IPT6 -A FORWARD -i $WAN -d $<internal machine>v6 -p tcp --dport 22 -j ACCEPT                                          # IPv6
$IPT -t nat -A PREROUTING -i $WAN -p tcp --dport 63663 -j DNAT --to $<internal machine>:63663                     #Skype
$IPT6 -A FORWARD -i $WAN -d $<internal machine>v6 -p tcp --dport 63663 -j ACCEPT                                     # IPv6

# These two redirect a block of ports, in both udp and tcp.
#$IPT -t nat -A PREROUTING -i $WAN -p tcp --dport 2300:2400 -j DNAT --to 10.1.1.50
#$IPT -t nat -A PREROUTING -i $WAN -p udp --dport 2300:2400 -j DNAT --to 10.1.1.50


# Now, our firewall chain. We use the limit commands to 
# cap the rate at which it alerts to 15 log messages per minute.
$IPT -N firewall
$IPT -A firewall -m limit --limit 15/minute -j LOG --log-prefix Firewall:
$IPT -A firewall -j DROP
# IPv6
$IPT6 -N firewall
$IPT6 -A firewall -m limit --limit 15/minute -j LOG --log-prefix Firewall:
$IPT6 -A firewall -j DROP

# Now, our dropwall chain, for the final catchall filter.
$IPT -N dropwall
$IPT -A dropwall -m limit --limit 15/minute -j LOG --log-prefix Dropwall:
$IPT -A dropwall -j DROP
# IPv6
$IPT6 -N dropwall
$IPT6 -A dropwall -m limit --limit 15/minute -j LOG --log-prefix Dropwall:
$IPT6 -A dropwall -j DROP

# Our "hey, them's some bad tcp flags!" chain.
$IPT -N badflags
$IPT -A badflags -m limit --limit 15/minute -j LOG --log-prefix Badflags:
$IPT -A badflags -j DROP
# IPv6
$IPT6 -N badflags
$IPT6 -A badflags -m limit --limit 15/minute -j LOG --log-prefix Badflags:
$IPT6 -A badflags -j DROP

# And our silent logging chain.
$IPT -N silent
$IPT -A silent -j DROP
# IPv6
$IPT6 -N silent
$IPT6 -A silent -j DROP

# This rule will accept connections from local machines. If you have
# a home network, enter in the IP's of the machines on the 
# network below.
$IPT -A INPUT -i lo -j ACCEPT
$IPT -A INPUT -i $LAN -s $LAN_NET -d 0/0 -p all -j ACCEPT
$IPT -A INPUT -i $DMZ -s $DMZ_NET -d 0/0 -p all -j ACCEPT
$IPT -A INPUT -i $UNT -s $UNT_NET -d 0/0 -p all -j ACCEPT

# IPv6 Unlimited access loopback
$IPT6 -A INPUT -i lo -j ACCEPT
$IPT6 -A OUTPUT -o lo -j ACCEPT

#Slow connection based attacks
$IPT -I INPUT -p tcp --dport 22 -i $WAN -m state --state NEW -m recent --set
$IPT -I INPUT -p tcp --dport 22 -i $WAN -m state --state NEW -m recent --update --seconds 60 --hitcount 5 -j dropwall
$IPT -I INPUT -p tcp --dport <Internet port for ssh to internal machine> -i $WAN -m state --state NEW -m recent --set
$IPT -I INPUT -p tcp --dport <Internet port for ssh to internal machine> -i $WAN -m state --state NEW -m recent --update --seconds 60 --hitcount 5 -j dropwall
# IPv6
$IPT6 -I INPUT -p tcp --dport 22 -i $WAN -m state --state NEW -m recent --set
$IPT6 -I INPUT -p tcp --dport 22 -i $WAN -m state --state NEW -m recent --update --seconds 60 --hitcount 5 -j dropwall
$IPT6 -I FORWARD -p tcp --dport 22 -i $WAN -m state --state NEW -m recent --set
$IPT6 -I FORWARD -p tcp --dport 22 -i $WAN -m state --state NEW -m recent --update --seconds 60 --hitcount 5 -j dropwall

# Drop those nasty packets! These are all TCP flag 
# combinations that should never, ever occur in the
# wild. All of these are illegal combinations that 
# are used to attack a box in various ways, so we 
# just drop them and log them here.
$IPT -A INPUT -p tcp --tcp-flags ALL FIN,URG,PSH -j badflags
$IPT -A INPUT -p tcp --tcp-flags ALL ALL -j badflags
$IPT -A INPUT -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j badflags
$IPT -A INPUT -p tcp --tcp-flags ALL NONE -j badflags
$IPT -A INPUT -p tcp --tcp-flags SYN,RST SYN,RST -j badflags
$IPT -A INPUT -p tcp --tcp-flags SYN,FIN SYN,FIN -j badflags
# IPv6
$IPT6 -A INPUT -p tcp --tcp-flags ALL FIN,URG,PSH -j badflags
$IPT6 -A INPUT -p tcp --tcp-flags ALL ALL -j badflags
$IPT6 -A INPUT -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j badflags
$IPT6 -A INPUT -p tcp --tcp-flags ALL NONE -j badflags
$IPT6 -A INPUT -p tcp --tcp-flags SYN,RST SYN,RST -j badflags
$IPT6 -A INPUT -p tcp --tcp-flags SYN,FIN SYN,FIN -j badflags
# IPv6 Forward
$IPT6 -A FORWARD -p tcp --tcp-flags ALL FIN,URG,PSH -j badflags
$IPT6 -A FORWARD -p tcp --tcp-flags ALL ALL -j badflags
$IPT6 -A FORWARD -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j badflags
$IPT6 -A FORWARD -p tcp --tcp-flags ALL NONE -j badflags
$IPT6 -A FORWARD -p tcp --tcp-flags SYN,RST SYN,RST -j badflags
$IPT6 -A FORWARD -p tcp --tcp-flags SYN,FIN SYN,FIN -j badflags

# Drop icmp, but only after letting certain types through.
$IPT -A INPUT -p icmp --icmp-type 0 -j ACCEPT
$IPT -A INPUT -p icmp --icmp-type 3 -j ACCEPT
$IPT -A INPUT -p icmp --icmp-type 11 -j ACCEPT
$IPT -A INPUT -p icmp --icmp-type 8 -m limit --limit 1/second -j ACCEPT
$IPT -A INPUT -p icmp -j firewall

# If you would like to open up port 22 (SSH Access) to various IP's
# simply edit the IP's below and uncomment the line. If you wish to 
# enable SSH access from anywhere, uncomment the second line only. 
#$IPT -A INPUT -i $WAN -s 10.1.1.1 -d 0/0 -p tcp --dport 22 -j ACCEPT
#$IPT -A INPUT -i $WAN -s 0/0 -d 0/0 -p tcp --dport 22 -j ACCEPT

# If you are running a Web Server, uncomment the next line to open
# up port 80 on your machine.
#$IPT -A INPUT -i $WAN -s 0/0 -d 0/0 -p tcp --dport 80 -j ACCEPT
$IPT -A INPUT -i $WAN -s 0/0 -d 0/0 -p udp --dport 1194 -j ACCEPT       #OpenVPN
$IPT6 -A INPUT -i $WAN -s 0/0 -d 0/0 -p udp --dport 1194 -j ACCEPT      # IPv6
$IPT6 -A INPUT -i $WAN -s 0/0 -d 0/0 -p udp --dport 546 -j ACCEPT       #DHCPv6 client
$IPT -A INPUT -i $WAN -s 0/0 -d 0/0 -p udp --dport 5353 -j ACCEPT       #mDNS
$IPT6 -A INPUT -i $WAN -s 0/0 -d 0/0 -p udp --dport 5353 -j ACCEPT      #mDNS
$IPT -A INPUT -i $WAN -s 0/0 -d 0/0 -p udp --dport 68 -j ACCEPT          #Bootpc

# Lets do some basic state-matching. This allows us 
# to accept related and established connections, so
# client-side things like ftp work properly, for example.
$IPT -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Uncomment to drop port 137 netbios packets silently. 
# We don't like that netbios stuff, and it's way too 
# spammy with windows machines on the network.
$IPT -A INPUT -p udp --sport 137 --dport 137 -j silent

# Our final trap. Everything on INPUT goes to the dropwall 
# so we don't get silent drops.
$IPT -A INPUT -j dropwall

# NAT addresses between the VPN and the internal network in order to avoid common address clashes
$IPT -t nat -A PREROUTING -i tun0 -d 10.<x>.<x>.0/24 -j NETMAP --to $LAN_NET
$IPT -t nat -A POSTROUTING -o tun0 -s $LAN_NET -j NETMAP --to 10.<x>.<x>.0/24
$IPT -t nat -A POSTROUTING -o eth0 -s 10.<x>.<x>.0/24 -j NETMAP --to $LAN_NET
#echo 1 > /proc/sys/net/ipv4/conf/tun0/proxy_arp
#echo 1 > /proc/sys/net/ipv4/conf/eth0/proxy_arp

# IPv6 Log everything else
$IPT6 -A INPUT -i $WAN -j LOG
$IPT6 -A INPUT -i $WAN -j DROP

```

2. Drop IPv4 firewall rules script:
```

# The location of the IPtables binary file on your system.
IPT="/sbin/iptables"

# The Network Interface you will be protecting. For ADSL/dialup users,
# ppp0 should be fine. If you are using a cable internet connection or
# are connected to a LAN, you will have to change this to "eth0".
WAN="wlan0"
LAN="eth0"

# The following rules will clear out any existing firewall rules, 
# and any chains that might have been created.
$IPT -F
$IPT -F INPUT
$IPT -F OUTPUT
$IPT -F FORWARD

```

3. Drop IPv6 firewall rules script (good idea to break this out for individual IP stack debugging):
```

# The location of the IPtables binary file on your system.
IPT6="/sbin/ip6tables"

# The Network Interface you will be protecting. For ADSL/dialup users,
# ppp0 should be fine. If you are using a cable internet connection or
# are connected to a LAN, you will have to change this to "eth0".
WAN="wlan0"
LAN="eth0"

# The following rules will clear out any existing firewall rules, 
# and any chains that might have been created.
$IPT6 -F
$IPT6 -X
$IPT6 -P INPUT ACCEPT
$IPT6 -P FORWARD ACCEPT
$IPT6 -P OUTPUT ACCEPT

```

4. Setup packet prioritization.  Adapted from: [http://wiki.linuxwall.info/doku.php/en:ressources:dossiers:networking:traffic_control](http://wiki.linuxwall.info/doku.php/en:ressources:dossiers:networking:traffic_control)
    and [https://github.com/jvehent/lnw-tc/blob/master/lnw_gateway_tc.sh](https://github.com/jvehent/lnw-tc/blob/master/lnw_gateway_tc.sh)
  a. Go to /etc/network.
  b. Create file lnw_gateway_tc.sh:
```

#! /usr/bin/env bash
#
### BEGIN INIT INFO
# Provides: lnw_gateway_qos.sh
# Required-Start: $syslog
# Required-Stop: $syslog
# Should-Start: $local_fs
# Should-Stop: $local_fs
# Default-Start: 2
# Default-Stop: 0 1 6
# Short-Description: starts/stops lnw_gateway_qos.sh
# Description: load or stop the Traffic Control rules on the network interface
### END INIT INFO

WAN=eth<y> # network card to apply the QoS to
LAN=eth<x>
UPLINK=<my measured upload speed sans a few kb for consistency sake> # upload in kbits/s
DOWNLINK=<my measured download speed sans a few mb for consistency sake> # download in kbits/s

TC=/sbin/tc
IPT=/sbin/iptables
IPT6=/sbin/ip6tables

case "$1" in
        start)
                echo "~~~~ LOADING $WAN TRAFFIC CONTROL RULES FOR `uname -n` ~~~~"

                # WAN side
                echo "#-Outgoing WAN"
                # the r2q value is calculated to let ~3 full packets pass before
                # rescheduling, so r2q = (UPLINK / (3 * MTU * 8))
                echo "#-define a HTB root qdisc"
                $TC qdisc add dev $WAN root handle 1: htb default 999 r2q 40

                # this is the main branch that sets the total bandwidth available to the leaves
                echo "#--uplink - rate $UPLINK kbit ceil $UPLINK kbit"
                $TC class add dev $WAN parent 1:0 classid 1:1 htb \
                        rate $(($UPLINK))kbit ceil $(($UPLINK))kbit

                # INTERACTIVE CLASS: for low latency, high priority packets such as VoIP and DNS
                # it has little bandwidth assigned to it, but pass before everything else
                echo "#---interactive - id 100 - rate $(( $UPLINK / 10 )) kbit ceil $(( $UPLINK / 10 * 8 )) kbit"
                $TC class add dev $WAN parent 1:1 classid 1:100 htb \
                        rate $(( $UPLINK / 10 ))kbit ceil $(( $UPLINK / 10 * 8 ))kbit \
                        burst 5k prio 1

                # this class transmits using a pfifo before exiting
                echo "#--- ~ sub interactive: pfifo"
                $TC qdisc add dev $WAN parent 1:100 handle 1100: pfifo limit 10

                # filter definition that will catch all the packets carrying the mark 100
                echo "#--- ~ interactive filter"
                $TC filter add dev $WAN parent 1:0 protocol ip prio 1 \
                        handle 100 fw flowid 1:100

                # netfilter/iptables rules, will mark all UDP packets
                echo "#--- ~ netfilter rule - all UDP traffic at 100"
                $IPT -t mangle -A POSTROUTING -o $WAN -p udp -j CONNMARK --set-mark 100
                $IPT6 -t mangle -A POSTROUTING -o $WAN -p udp -j CONNMARK --set-mark 100

                # TCP ACKs class: it's important to let the ACKs leave the network as fast as possible
                # when a host on the network is downloading.
                echo "#---tcp acks - id 200 - rate $(( $UPLINK / 5 )) kbit ceil $(( $UPLINK )) kbit"
                $TC class add dev $WAN parent 1:1 classid 1:200 htb \
                rate $(( $UPLINK / 5 ))kbit ceil $(( $UPLINK / 10 ))kbit burst 15k prio 2
                echo "#--- ~ sub tcp acks: sfq"
                $TC qdisc add dev $WAN parent 1:200 handle 1200: sfq perturb 10 limit 32
                echo "#--- ~ filtre tcp acks"
                $TC filter add dev $WAN parent 1:0 protocol ip prio 2 handle 200 fw flowid 1:200
                echo "#--- ~ netfilter rule for TCP ACKs will be loaded at the end"

                # SSH class: for outgoing connections to avoid lag when somebody else is downloading
                # however, an SSH connection cannot fill up the connection to more than 80%
                echo "#---ssh - id 300 - rate $(( $UPLINK / 10 )) kbit ceil $(( $UPLINK / 10 * 8 )) kbit"
                $TC class add dev $WAN parent 1:1 classid 1:300 htb \
                rate $(( $UPLINK / 10 ))kbit ceil $(( $UPLINK / 10 * 8 ))kbit burst 15k prio 3

                # SFQ (Stochastic Fair Queuing) will mix the packets if there are several SSH
                #  connections in parallel and ensure that none has the priority.
                echo "#--- ~ sub ssh: sfq"
                $TC qdisc add dev $WAN parent 1:300 handle 1300: sfq perturb 10 limit 32
                echo "#--- ~ ssh filter"
                $TC filter add dev $WAN parent 1:0 protocol ip prio 3 handle 300 fw flowid 1:300
                echo "#--- ~ netfilter rule - SSH at 300"
                $IPT -t mangle -A POSTROUTING -o $WAN -p tcp --tcp-flags SYN SYN \
                        --dport 22 -j CONNMARK --set-mark 300
                $IPT6 -t mangle -A POSTROUTING -o $WAN -p tcp --tcp-flags SYN SYN \
                        --dport 22 -j CONNMARK --set-mark 300

                # HTTP class: All web browsing (80/443) gets half the bandwidth and can borrow full
                echo "#---http branch - id 400 - rate $(( $UPLINK / 2 )) kbit ceil $UPLINK kbit"
                $TC class add dev $WAN parent 1:1 classid 1:400 htb \
                rate $(( $UPLINK / 2 ))kbit ceil $(( $UPLINK ))kbit burst 30k prio 4
                echo "#--- ~ sub http branch: sfq"
                $TC qdisc add dev $WAN parent 1:400 handle 1400: sfq perturb 10 limit 32
                echo "#--- ~ http branch filter"
                $TC filter add dev $WAN parent 1:0 protocol ip prio 4 handle 400 fw flowid 1:400
                echo "#--- ~ netfilter rule - http/s"
                $IPT -t mangle -A POSTROUTING -o $WAN -p tcp --tcp-flags SYN SYN \
                        --dport 80 -j CONNMARK --set-mark 400
                $IPT -t mangle -A POSTROUTING -o $WAN -p tcp --tcp-flags SYN SYN \
                        --dport 443 -j CONNMARK --set-mark 400
                $IPT6 -t mangle -A POSTROUTING -o $WAN -p tcp --tcp-flags SYN SYN \
                        --dport 80 -j CONNMARK --set-mark 400
                $IPT6 -t mangle -A POSTROUTING -o $WAN -p tcp --tcp-flags SYN SYN \
                        --dport 443 -j CONNMARK --set-mark 400

                # DEFAULT Class: the root qdisc will send all non filtered traffic to this one
                # we also set a netfilter rule to send large file transfers to this queue
                # and avoid impacting the HTTP queue
                echo "#---default - id 999 - rate $(( $UPLINK / 10 ))kbit ceil $(( $UPLINK ))kbit"
                $TC class add dev $WAN parent 1:1 classid 1:999 htb \
                        rate $(( $UPLINK / 10 ))kbit ceil $(( $UPLINK ))kbit burst 2k prio 9
                echo "#--- ~ sub default: sfq"
                $TC qdisc add dev $WAN parent 1:999 handle 1999: sfq perturb 10 limit 32
                echo "#--- ~ filtre default"
                $TC filter add dev $WAN parent 1:0 protocol ip prio 99 handle 999 fw flowid 1:999
                $IPT -t mangle -A POSTROUTING -o $WAN -p tcp -m connbytes --connbytes 10000000: \
                        --connbytes-mode bytes --connbytes-dir both -j CONNMARK --set-mark 999
                $IPT6 -t mangle -A POSTROUTING -o $WAN -p tcp -m connbytes --connbytes 10000000: \
                        --connbytes-mode bytes --connbytes-dir both -j CONNMARK --set-mark 999
                echo "#--- ~ propagating marks on connections"
                $IPT -t mangle -A POSTROUTING -j CONNMARK --restore-mark
                $IPT6 -t mangle -A POSTROUTING -j CONNMARK --restore-mark
                echo "#--- ~ Mark TCP ACKs flags at 200"
                $IPT -t mangle -A POSTROUTING -p tcp --tcp-flags URG,ACK,PSH,RST,SYN,FIN ACK \
                        -m length --length 40:64 -j MARK --set-mark 200
                $IPT6 -t mangle -A POSTROUTING -p tcp --tcp-flags URG,ACK,PSH,RST,SYN,FIN ACK \
                        -m length --length 40:64 -j MARK --set-mark 200


                # LAN side
                echo "#Incoming LAN"
                # the r2q value is calculated to let ~3 full packets pass before
                # rescheduling, so r2q = (UPLINK / (3 * MTU * 8))
                echo "#-define a HTB root qdisc"
                $TC qdisc add dev $LAN root handle 1: htb default 999 r2q 40

                # this is the main branch that sets the total bandwidth available to the leaves
                echo "#--uplink - rate $DOWNLINK kbit ceil $DOWNLINK kbit"
                $TC class add dev $LAN parent 1:0 classid 1:1 htb \
                        rate $(($DOWNLINK))kbit ceil $(($DOWNLINK))kbit

                # INTERACTIVE CLASS: for low latency, high priority packets such as VoIP and DNS
                # it has little bandwidth assigned to it, but pass before everything else
                echo "#---interactive - id 100 - rate $(( $DOWNLINK / 10 )) kbit ceil $(( $DOWNLINK / 10 * 8 )) kbit"
                $TC class add dev $LAN parent 1:1 classid 1:100 htb \
                        rate $(( $DOWNLINK / 10 ))kbit ceil $(( $DOWNLINK / 10 * 8 ))kbit \
                        burst 5k prio 1

                # this class transmits using a pfifo before exiting
                echo "#--- ~ sub interactive: pfifo"
                $TC qdisc add dev $LAN parent 1:100 handle 1100: pfifo limit 10

                # filter definition that will catch all the packets carrying the mark 100
                echo "#--- ~ interactive filter"
                $TC filter add dev $LAN parent 1:0 protocol ip prio 1 \
                        handle 100 fw flowid 1:100

                # netfilter/iptables rules, will mark all UDP packets
                echo "#--- ~ netfilter rule - all UDP traffic at 100"
                $IPT -t mangle -A POSTROUTING -o $LAN -p udp -j CONNMARK --set-mark 100
                $IPT6 -t mangle -A POSTROUTING -o $LAN -p udp -j CONNMARK --set-mark 100

                # TCP ACKs class: it's important to let the ACKs leave the network as fast as possible
                # when a host of the network is downloading.
                echo "#---tcp acks - id 200 - rate $(( $DOWNLINK / 5 )) kbit ceil $(( $DOWNLINK )) kbit"
                $TC class add dev $LAN parent 1:1 classid 1:200 htb \
                rate $(( $DOWNLINK / 5 ))kbit ceil $(( $DOWNLINK / 10 ))kbit burst 15k prio 2
                echo "#--- ~ sub tcp acks: sfq"
                $TC qdisc add dev $LAN parent 1:200 handle 1200: sfq perturb 10 limit 32
                echo "#--- ~ filtre tcp acks"
                $TC filter add dev $LAN parent 1:0 protocol ip prio 2 handle 200 fw flowid 1:200
                echo "#--- ~ netfilter rule for TCP ACKs will be loaded at the end"

                # SSH class: for outgoing connections to avoid lag when somebody else is downloading
                # however, an SSH connection cannot fill up the connection to more than 80%
                echo "#---ssh - id 300 - rate $(( $DOWNLINK / 10 )) kbit ceil $(( $DOWNLINK / 10 * 8 )) kbit"
                $TC class add dev $LAN parent 1:1 classid 1:300 htb \
                rate $(( $DOWNLINK / 10 ))kbit ceil $(( $DOWNLINK / 10 * 8 ))kbit burst 15k prio 3

                # SFQ will mix the packets if there are several SSH connections in parallel
                # and ensure that none has the priority
                echo "#--- ~ sub ssh: sfq"
                $TC qdisc add dev $LAN parent 1:300 handle 1300: sfq perturb 10 limit 32
                echo "#--- ~ ssh filter"
                $TC filter add dev $LAN parent 1:0 protocol ip prio 3 handle 300 fw flowid 1:300
                echo "#--- ~ netfilter rule - SSH at 300"
                $IPT -t mangle -A POSTROUTING -o $LAN -p tcp --tcp-flags SYN SYN \
                        --dport 22 -j CONNMARK --set-mark 300
                $IPT6 -t mangle -A POSTROUTING -o $LAN -p tcp --tcp-flags SYN SYN \
                        --dport 22 -j CONNMARK --set-mark 300

                # HTTP class: All web browsing (80/443) gets half the bandwidth and can borrow full
                echo "#---http branch - id 400 - rate $(( $DOWNLINK / 2 )) kbit ceil $DOWNLINK kbit"
                $TC class add dev $LAN parent 1:1 classid 1:400 htb \
                rate $(( $DOWNLINK / 2 ))kbit ceil $(( $DOWNLINK ))kbit burst 30k prio 4
                echo "#--- ~ sub http branch: sfq"
                $TC qdisc add dev $LAN parent 1:400 handle 1400: sfq perturb 10 limit 32
                echo "#--- ~ http branch filter"
                $TC filter add dev $LAN parent 1:0 protocol ip prio 4 handle 400 fw flowid 1:400
                echo "#--- ~ netfilter rule - http/s"
                $IPT -t mangle -A POSTROUTING -o $LAN -p tcp --tcp-flags SYN SYN \
                        --dport 80 -j CONNMARK --set-mark 400
                $IPT -t mangle -A POSTROUTING -o $LAN -p tcp --tcp-flags SYN SYN \
                        --dport 443 -j CONNMARK --set-mark 400
                $IPT6 -t mangle -A POSTROUTING -o $LAN -p tcp --tcp-flags SYN SYN \
                        --dport 80 -j CONNMARK --set-mark 400
                $IPT6 -t mangle -A POSTROUTING -o $LAN -p tcp --tcp-flags SYN SYN \
                        --dport 443 -j CONNMARK --set-mark 400

                # DEFAULT Class: the root qdisc will send all non filtered traffic to this one
                # we also set a netfilter rule to send large file transfert to this queue
                # and avoid impacting the HTTP queue
                echo "#---default - id 999 - rate $(( $UPLINK / 10 ))kbit ceil $(( $UPLINK ))kbit"
                $TC class add dev $LAN parent 1:1 classid 1:999 htb \
                        rate $(( $DOWNLINK / 10 ))kbit ceil $(( $DOWNLINK ))kbit burst 2k prio 9
                echo "#--- ~ sub default: sfq"
                $TC qdisc add dev $LAN parent 1:999 handle 1999: sfq perturb 10 limit 32
                echo "#--- ~ filtre default"
                $TC filter add dev $LAN parent 1:0 protocol ip prio 99 handle 999 fw flowid 1:999
                $IPT -t mangle -A POSTROUTING -o $LAN -p tcp -m connbytes --connbytes 10000000: \
                        --connbytes-mode bytes --connbytes-dir both -j CONNMARK --set-mark 999
                $IPT6 -t mangle -A POSTROUTING -o $LAN -p tcp -m connbytes --connbytes 10000000: \
                        --connbytes-mode bytes --connbytes-dir both -j CONNMARK --set-mark 999
                echo "#--- ~ propagating marks on connections"
                $IPT -t mangle -A POSTROUTING -j CONNMARK --restore-mark
                $IPT6 -t mangle -A POSTROUTING -j CONNMARK --restore-mark
                echo "#--- ~ Mark TCP ACKs flags at 200"
                $IPT -t mangle -A POSTROUTING -p tcp --tcp-flags URG,ACK,PSH,RST,SYN,FIN ACK \
                        -m length --length 40:64 -j MARK --set-mark 200
                $IPT6 -t mangle -A POSTROUTING -p tcp --tcp-flags URG,ACK,PSH,RST,SYN,FIN ACK \
                        -m length --length 40:64 -j MARK --set-mark 200

                echo
                echo "Traffic Control is up and running"
                echo
        ;;
        stop)
                $IPT -t mangle -F
                $IPT -t mangle -X
                $IPT6 -t mangle -F
                $IPT6 -t mangle -X
                echo "iptables rules removed"
                #$TC qdisc del dev $WAN root handle 1
                $TC qdisc del dev $WAN root
                $TC qdisc del dev $LAN root
                echo "traffic control rules removed"
                exit 0
                ;;
        restart)
                $0 stop
                $0 start
                exit 0
                ;;
        show)
                echo;echo " ---- qdiscs details -----"
                $TC -d qdisc show dev $WAN
                echo;echo " ---- qdiscs statistics --"
                $TC -s qdisc show dev $WAN
                exit 0
                ;;
        *)
                echo;echo "usage:$0 {start|stop|restart|show}"
                echo "load or stop the Traffic Control rules on the network interface"
        ;;
esac

```

5. Add firewall and traffic control scripts to rc.local:
```

# Start firewall rules
/root/scripts/iptables-firewall.sh
/etc/network/lnw_gateway_tc.sh start

```

VI. Add IPv6 support (Comcast).  Adapted from: [http://blog.kylemanna.com/ipv6/2013/09/29/using-native-ipv6-via-comcast-in-san-francisco/](http://blog.kylemanna.com/ipv6/2013/09/29/using-native-ipv6-via-comcast-in-san-francisco/)
1. See rules in firewall script.  There are a few set parameters and so I just put them into the iptable rules script for easy tracking.

2. `apt-get install wide-dhcpv6-client`

3. Edit /etc/wide-dhcpv6/dhcp6c.conf:
```

# Default dhpc6c configuration: it assumes the address is autoconfigured using
# router advertisements.

interface eth<y> {
        send ia-na 1;
        send ia-pd 1;
        #Don't send rapid-commit on Comcast.  It causes only /64 prefix to be returned when we want a /60 prefix for multiple subnets.  Works on Cox.
        request domain-name-servers;
        request domain-name;

        script "/etc/wide-dhcpv6/dhcp6c-script";
};

id-assoc na 1 {
};

id-assoc pd 1 {
        prefix ::/60 infinity;

        prefix-interface eth<x> {
                sla-len 4;
                sla-id 0;
                ifid 10;
        };

        prefix-interface eth<x>.<a> {
                sla-len 4;
                sla-id 1;
                ifid 11;
        };

        prefix-interface eth<x>.<b> {
                sla-len 4;
                sla-id 2;
                ifid 12;
        };

};

```

4. `service wide-dhcpv6-client restart`

5. Wait about 15 seconds and then run:
```

`ip -6 addr ls`
`ip -6 route ls`

```
  If all is well, you will have Internet accessible IPv6 addresses, not just local link (fe80::) addresses.

6a. Make sure routes are advertised (dnsmasq method):
   a. `apt-get install dnsmasq`
   b. edit /etc/dnsmasq/ipv6:
```

dhcp-range=::a,constructor:eth<x>,ra-names,1d
dhcp-range=::b,constructor:eth<x>.<a>,ra-names,1d
dhcp-range=::c,constructor:eth<x>.<b>,ra-names,1d
enable-ra

```

7a. `service dnsmasq restart`

6b. Make sure routes are advertised (dadvd method.  Preferred method, especially if you don't need the extra dnsmasq services.):
   a. `apt-get install radvd`
   b. edit /etc/radvd.conf
```

interface eth<x> { # LAN interface
        AdvManagedFlag off; # no DHCPv6 server here.
        AdvOtherConfigFlag off; # not even for options.
        AdvSendAdvert on;
        AdvDefaultPreference high;
        AdvLinkMTU 1280;
        prefix ::/64 #pick one non-link-local prefix assigned to the interface and start advertising it
        {
                AdvOnLink on;
                AdvAutonomous on;
        };
};

interface eth<x>.<a> { # LAN interface
        AdvManagedFlag off; # no DHCPv6 server here.
        AdvOtherConfigFlag off; # not even for options.
        AdvSendAdvert on;
        AdvDefaultPreference high;
        AdvLinkMTU 1280;
        prefix ::/64 #pick one non-link-local prefix assigned to the interface and start advertising it
        {
                AdvOnLink on;
                AdvAutonomous on;
        };
};

interface eth<x>.<b> { # LAN interface
        AdvManagedFlag off; # no DHCPv6 server here.
        AdvOtherConfigFlag off; # not even for options.
        AdvSendAdvert on;
        AdvDefaultPreference high;
        AdvLinkMTU 1280;
        prefix ::/64 #pick one non-link-local prefix assigned to the interface and start advertising it
        {
                AdvOnLink on;
                AdvAutonomous on;
        };
};

```

7b. `service dadvd restart`

VII. Get dhcp (IPv4) server going:
1. `apt-get install isc-dhcp-server -y`

2. Edit /etc/default/isc-dhcp-server
    Make sure INTERFACES points only to your internal network(s).  May make ISP angry otherwise.

3. Edit /etc/dhcp/dhcpd.conf - This file is pretty self explanatory.  Just make sure all of the options you are going to feed to your internal machines are here.  Would also recommend setting up the static IP addresses section for any machines running services, especially if you are going to poke holes in your firewall to get to them.  If you have a network printer, life will be a lot easier with an entry for it in the static IP section.  Remember this is only IPv4.  IPv6 does a combination of local link addresses based on MAC addresses and Internet accessible IPs and IP address ranges assigned by your ISP and setup in section 6.

4. When ready, shut down any existing DHCP servers on your local network as two don't play well together.  Then run `service isc-dhcp-server restart`


VIII. Get Dynamic DNS going as it is nice to get to always be able to get to your box when away from home without worry that your IP address has changed.  (Have not found native IPv6 support in Ubuntu yet, but looks like some 3rd parties have been doing some hacking if I ever dare to run their code.)
1. Install ddclient - `apt-get install ddclient`

2. Edit /etc/ddclient.conf (I am using nyndns.com):
```

# Configuration file for ddclient generated by debconf
#
# /etc/ddclient.conf

protocol=dyndns2
use=web, web=checkip.dyndns.com, web-skip='IP Address'
server=members.dyndns.org
login=<login name>
password='<password>'
<domain name>

```

3. `service ddclient restart`

IX. Get OpenVPN tunnel going (only IPv4 for me at this point.  Having trouble getting it to work with IPv6.)
1. Adapted from: [https://help.ubuntu.com/14.04/serverguide/openvpn.html](https://help.ubuntu.com/14.04/serverguide/openvpn.html)

2. Extra help for IP collision avoidance NAT settings: [http://www.nimlabs.org/dirtynat.html](http://www.nimlabs.org/dirtynat.html)

3.  Some of the rules, such as the NAT to avoid IP collisions (say you are at your friend's house and their IPv4 subnet is 192.168.0.0 while yours is also 192.168.0.0) I have in my firewall rules script.

4. Follow main guide to get keys setup and basic configuration.  A special thing I do is in the main server.conf file, I push the NATed IP subnet I created in my firewall rules so the machines VPNing in can find the computers on the local network.  So for example instead of typing in `ping 192.168.<x>.<x>` to get to one of my internal computers from the VPN, I type in `ping 10.<x>.<x>.<x>` and have the 10.<x>.<x>.0 route in my push rules.

X. Todo list
1. Get fwknop SPA (single packet authentication) going to better protect forwarded services.
2. Get IPv6 working with OpenVPN.
3. Get IPv6 Dynamic DNS going.
4. Improve firewall monitoring methods.

Well let me know what you think and feel free to share tips.  This is an exercise of the most direct control over my gateway to the outside world.  I know there are easier ways, but where is the fun in that and how can you make sure it is being done right?

---

### Post by TheFu on 2015-05-25
code tags for the code parts would help.
I'm using pfsense with a $100 AMD e-350 box.
Comcast doesn't support IPv6 here and I'm on business class. Been trying to get it for years. Heard they were giving out /54 spaces.

---

### Post by BatteryKing on 2015-05-25
OK.  I added code tags.  Much better.

Maybe Comcast is saving business class for last?  One thing I came across is my Ubuntu firewall did not grab any IPv6 addresses from Comcast until I explicitly setup wide-dhcpv6 and mDNS (mDNS is not the only method).  The only way I found out IPv6 was on my segment was one day my wireless Netgear router turned into just an AP had the IPv6 setting enabled and managed to grab a subnet for my network, but of course acting only as an AP it was not actually routable.  (I figure it must of talked over IPv4 because there was no IPv6 route to Comcast at the time.)  The other gotcha I came across is with the firewall rules, I came across the wrong port information for DHCPv6 service and so after a few days the addresses would go away. I sniffed the traffic and found I needed UDP port 546 open.  Then I searched the RFC for 546 and confirmed this is the right port.  (I guess if I had taken the time to read the whole RFC in the first place I would have known.)

Only once the edge router is configured properly due all of the machines (both Windows and Linux) grab valid IPv6 addresses.

I suspect your problem is Comcast is taking its time to see how things go with their lower tiered service before promising things to the business folk where then they have to support any issues, but thought it would be good to mention this.

---

### Post by TheFu on 2015-05-25
Comcast business started IPv6 rollout about 5-6 yrs ago. I don't know why I don't have it here yet.  Perhaps I need to complain every month?  Got added to the "interested" list about 4 yrs ago.  Plus the comcast router (it is theirs and they manage it) is DOCSIS3, so IPv6 isn't an issue.  Perhaps they aren't rolling it out for multi-static-IP customers?  I dunno. My public subnet isn't anything too complicated.

[http://forums.businesshelp.comcast.com/t5/IPV6/When-is-static-IPv6-for-business-users-coming-out-in-Portland-OR/m-p/21402#U21402](http://forums.businesshelp.comcast.com/t5/IPV6/When-is-static-IPv6-for-business-users-coming-out-in-Portland-OR/m-p/21402#U21402) has the most honest answer I've seen.

Heck, Comcast promised they would do an account change for me 3 weeks ago - it required a signed document which I sent the same day. Followed up last Wednesday to see if it was done. It wasn't. The CSR escalated and promised 24 hr completion AND an email the following day after it was done.  Haven't heard a word.  Typical.  They just want to waste our time and hope we go away.  Our government really needs to force all cable providers with more than 50K customers to be open (share the infra) so we can actually get real customer service.  This way, smaller ISPs aren't impacted which have a reputation for listening to their clients, but all the big-boys are forced to become carriers and allow competition on their lines.

OTOH, the naked-DSL stuff never worked very well - AT&T only lets those folks offer the crappiest, slow, offerings and keep the 25Mbps+ offers for themselves.  At least I've never seen a DSL offer from the non-telco that was ADSL2+ anywhere here.

Having IPv6 addresses isn't an issue - those can be gotten from HE and tunneled through IPv4. I want NATIVE IPv6.

---

### Post by BatteryKing on 2015-05-26
I suppose there is a fundamental problem in that when a telco just has to have the basic equipment turned on and doing something, most people will still pay for it, so the telco really does not care beyond this.  It is not like there is competition in most places cause a mass switch over.

I have had a bit of a dodgy experience with U-verse.  They need to have the boxes close and at that I have found they often use cheap wire for short runs which still has too much interference / signal loss.  So maybe for some it works, but for many others it either is very lossy or AT&T won't offer it to you even though you are in a service area because it does not actually reach where you are.  If you look at how many people simply can't get U-verse in AT&T U-verse service areas, it is really kind of bad.  AT&T does not really seem to care if potential customers who call them and ask for the service in their service area can get it or not.  If their initial truck roll did not get you, well too bad.  If the wiring is dodgy, well too bad.  I see DSL in general as end of life because it just can't go the speed, it just does not have the reach at higher speeds, and the way AT&T manages it, it is really hit or miss whether it will really work or not.  I would think a business park would be a particularly bad place to do ADSL2+ because the big boys are going to do fiber and the small shops asking for it are going to be spaced too far apart for localized truck roles to be cost effective.  Probably the best thing for the telcos to do is to use the old T1 wiring as pull strings to pull fiber in, but that is not going to happen any time soon.

Coax at least has life left in it.  With a couple hundred MHz of spectrum they can push 10 Gb/s down and 1 Gb/s up with technology Comcast claims they are in the process of getting rolled out.  Just the question of interference on the segment and if your part of the segment is getting too much or too little signal.  Fiber is really nice, has the reach, and is reliable, but it seems like there is not too much interest to install it.  Actually as far as I can figure telcos would make more money in the long run if they just installed fiber everywhere because it is cheaper to maintain than any other technology in use and in many cases they could charge more for the higher speeds and people would pay for it.

---

### Post by BatteryKing on 2015-07-13
I came across a possible practical use for doing your own mini-ITX system described above with Comcast beyond just being paranoid about security enough to start your own firewall from scratch venture.  This would be to support Comcast's Gigabit Pro service if I understand its configuration correctly.  My unverified understanding (I can't seem to find an official source) is you need to have a 10 Gb capable NIC with an SFP port in order to handle the 2Gb/s speed offered.  You are not going to find this on your garden variety wireless router.  Hence putting together a mini-ITX system physically large enough to host a 10Gb/s PCIe NIC with an SFP port.  While I am not going to name specific parts, there is a particular method of part finding which I think will be most advantages to minimizing costs while still getting the advertised 2Gb/s speeds:

1. Mini-ITX board with a single PCIe slot and dual onboard NICs.  Linux can handle 802.3ad channel bonding on just about any NIC, so bonding the two onboard NICs should in theory provide the requisite speed through the custom firewall.

2. Managed 1 Gb/s Ethernet switch.  Most any managed switch can handle 802.3ad channel bonding and something sized for home use is not that much money, especially not much for anybody considering Comcast's Gigabit Pro service.  The ability to bond up to 4 ports (or more) is pretty common across the managed switches I have configured in the past and you only need to bond 2 in this case.

3. If your desktop is Linux and you have say a quality gaming board, you probably already have two 1 Gb/s ports.  Just configure Linux to bond these two ports and you should be good to go.

4. If your desktop is Windows well it is a little more tricky.  Windows Server 2012 and up should have support from what I have read and also some server based NICs have driver support.  Especially if you are running Windows Desktop, may want to poke around a little and make sure the server NIC you pick up for the task will work with your version of Windows and do the channel bonding.

5.  Especially with a managed switch, you can always have some devices just go at single 100/1000 Mb/s line rates.  I suppose if there are multiple people in the house all going at 1 Gb/s, you don't have to worry so much about somebody else in the house slowing things down by saturating their 1 Gb/s link because the total house bandwidth will be 2 Gb/s.  If you do mixed rates with different devices, may want to revisit the traffic control configuration I mention in the main post as the link to the slower home devices will be the bottleneck, not Internet connection.  Also probably want to make sure the switch has its own QoS support and that support is turned on.

The reason you would go the route with bonded 1Gb/s ports instead a single 10Gb/s link per device is 10Gb/s is expensive, especially if you have several devices to hook up to your home network.  A mini-ITX system with just enough space for a single PCIe card can be made to be compact, quiet, and relatively cheap.  I suppose you could get a dual port 10Gb/s card, but do make sure the m/b has enough PCIe lanes wired up to push it or go up to a micro-ATX board and do consider either two 10Gb/s cards or a dual port 10Gb/s card is probably a bit more than what a single 10Gb/s card is.  A managed 1Gb/s switch with channel bonding capabilities can be had for a small fraction of the cost of a 10Gb/s capable switch.  Of course if you have money to blow on Comcast's Gigabit Pro service, maybe you don't care about the additional cost of 10 Gb/s networking and already have it in your house.

---

### Post by TheFu on 2015-07-14
I was just looking at 10G networking yesterday.  The cheap NICs are $650.  Whereas the Intel PRO/1000 GigE NICs are $25 and I've seen dual and quad-port models for $40 and $100.  A managed GigE switch for home is between $80 and $200 - cheap. Most have backplanes that support 8Gbps and more.  

Every MB I've looked at recently had onboard GigE port(s). I think the 10/100 NICs only happens on laptops these days and don't know why. Just built a cheap microATX system with a $50 MB - it has a GigE port and 6 USB3 ports. Impressive little board, though I wish it had all SATA-3 ports instead of split 2/2 for SATA-3/2.

BTW, it has been 3 Comcast billing cycles now and the name change I formally requested (in writing, on THEIR form) in April hasn't happened yet.

---

### Post by BatteryKing on 2015-07-19
I made a couple of quick tweaks to the ports allowed to the firewall.  Specifically I added IPv4 access to UDP port 5353 as Comcast seems to want to hit for both IP protocols it looks like.  Also added UDP port 68 as while the service works without it, I noticed the Comcast DHCP server was probing on this port, so I figured might as well let it through.

At the time of this writing my IPv6 is not working right with Comcast.  It looks like their DHCPv6 server is no longer assigning subnets for me to use for my internal network(s), however their DHCPv6 server is providing a single address for the external network.  In other words I can surf the Internet in all of its IPv6 glory directly on the firewall, but not on my internal computers.  This internal subnet assignment is kind of important as NAT in terms of masquerading is not something you are supposed to do with IPv6, only a dirty IPv4 hack to extend its useful life.  With IPv6 you are supposed to have all public addresses and then use a real firewall and throw away dynamic addresses for your browsing as well as a more static address based on your MAC address.  I filed a level 2 ticket with them.  Kind of funny the first lady I talked to at Comcast thought "I P version 6" was a static IP address and was so insistent on it that she transferred me to the sales department trying to get me to buy a business account so I could have a static IP address.  I am just trying to surf the web here and don't need static addresses for that.  She tried to explain to me that with 'dynamic' addresses on the home account "maybe one week you will have the I P version 4 address and the next week you will have the I P version 6 address.  That is how dynamic addresses work."  At least after about 1 hour of getting bounced around and sitting on hold and going round and round with that lady, I eventually talked to someone knowledgeable enough to file a ticket for level 2 to look at.  As an update I talked to level 2 and they just told me to either get a new modem (my current one is on the IPv6 list, but apparently not a gold star) or hope that other people complain of the same problem as I am having before it will be looked at.  Makes me wonder how many people realize what IPv6 is and especially would even notice if IPv6 was working on their connection or not enough to call up and complain about it.

---

### Post by BatteryKing on 2015-11-26
Changed the original post to reflect changed in order to handle multiple VLANs each with their unique properties.  I did find a way to get the /60 prefix allocation so I can have 16 subnets to play with from Comcast and that is to not use rapid commit in WIDE DHCPv6.  The funny thing is rapid-commit used to work, however it seems to be broken on the Comcast side now as I sniffed the traffic and found the /60 prefix in the outgoing packet and /64 in the incoming packet.  With rapid commit turned off there are a couple more packets, but the response has a /60 subnet mask in it.

---

### Post by BatteryKing on 2016-03-20
I have moved and am now on the Cox network.  One nice thing about being on the Cox network is the wide-dhcpv6 option of rapid-commit seems to work.
One problem I am having is Cox stops routing to my internal subnets after 24 hours until I restart the wide-dhcpv6 client.  It does however work for just the /128 address on the firewall.  I have traced the problem down to the PD (Prefix Delegation) vltime (Valid Lifetime) parameter reply.  According to Wireshark, it reads the reply from Cox's server as 86,400 seconds (24 hours).  (The NA vltime for the /128 address is correct in both Wireshark and wide-dhcpv6.)  According to the extra verbose (-D option) wide-dhcpv6 debugging, the PD vltime is 140,733,193,474,432 seconds.  The value that wide-dhcpv6 is reading is definitely not right and explains why I have a problem.  The question is why is it fouling up?  The extra odd thing is this was reading on Comcast's network (I never looked because I did not have to), it was not a problem, which suggests it was probably working.  So the problem statement can be summarized as:
1. PD vltime was apparently read correctly by the wide-dhcpv6 client on Comcast's network.
2. PD vltime is read as the expected value by Wireshark on Cox's network.
3. PD vltime is read as an unexpected value by the wide-dhcpv6 client on Cox's network.

So what can I do from here?  (Do I just have to go through source and dork around or do I have another option?)

As a bit of an update I have started going through the source, but I have not figured out the problem yet, just narrowed it down.  In the Wireshark hex dump I just see the correct time of 0x00015180 and around it are other fields with their correct values.  The value being print out by wide-dhcpv6 is 0x7FFF00015180, so there are two extra bytes there apparently causing trouble.  The odd thing is it looks like an unsigned 32-bit int is explicitly used for the field, so I am not sure where these extra bytes are coming from.  I will have to think about that more.

Update: Filed a bug report here: [https://bugs.launchpad.net/ubuntu/+source/wide-dhcpv6/+bug/1559741](https://bugs.launchpad.net/ubuntu/+source/wide-dhcpv6/+bug/1559741)

---

