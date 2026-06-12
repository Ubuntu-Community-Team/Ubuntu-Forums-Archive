---
title: "Multiple Network Interfaces"
date: 2014-05-27
forum: Networking &amp; Wireless
---

### Post by christopher12 on 2014-05-27
Hello Everyone, 

So I am currently setting up a new Ubuntu Server for our office. 

It is replacing our old cent os server. 

The old server had three network interfaces which we had connected as follows

eth0 - connected to a static ip address (fiber optic internet connection) We would use this to upload files 
eth1 - connected dhcp to our broadband internet we would use this for our companies internet surfing
eth2 - connected to our internal internet (static ip) The server is running a dhcp/dns server off of this card.


So the new server I am trying to set up the same configuration. 
```

#Fiber
auto eth0iface eth0 inet static
address XXX.XX.XXX.XX
network XXX.XX.XXX.X
netmask 255.255.255.XXX
braodcast XXX.XX.XXX.X


#Broadband
auto eth1
iface eth1 inet dhcp


#Internal
auto eth2
iface eth2 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
```

So I went through this documentation. 
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

And I have been able to get the dhcp and the ddns working. All of the computers in the office are able to surf the internet just fine. 

So my problem right now is getting the computer to recognize the Fiber connection. 

I can't seem to send out pings from that card.

So my question is. Do I have to set up routing information for this? 

If I am correct I am currently routing all the internet traffic from the script nat.sh from the routing documentation (posted above)

```

[LIST]
[*=left]echo -e "\n\nLoading simple rc.firewall-iptables version $FWVER..\n"
[FONT=inherit][/FONT]DEPMOD=/sbin/depmod
[FONT=inherit][/FONT]MODPROBE=/sbin/modprobe
[FONT=inherit][/FONT]
[FONT=inherit][/FONT]EXTIF="eth1"
[FONT=inherit][/FONT]INTIF="eth2"
[FONT=inherit][/FONT]#INTIF2="eth0"
[FONT=inherit][/FONT]echo "   External Interface:  $EXTIF"
[FONT=inherit][/FONT]echo "   Internal Interface:  $INTIF"
[FONT=inherit][/FONT]
[FONT=inherit][/FONT]#======================================================================
[FONT=inherit][/FONT]#== No editing beyond this line is required for initial MASQ testing == 
[FONT=inherit][/FONT]echo -en "   loading modules: "
[FONT=inherit][/FONT]echo "  - Verifying that all kernel modules are ok"
[FONT=inherit][/FONT]$DEPMOD -a
[FONT=inherit][/FONT]echo "----------------------------------------------------------------------"
[FONT=inherit][/FONT]echo -en "ip_tables, "
[FONT=inherit][/FONT]$MODPROBE ip_tables
[FONT=inherit][/FONT]echo -en "nf_conntrack, " 
[FONT=inherit][/FONT]$MODPROBE nf_conntrack
[FONT=inherit][/FONT]echo -en "nf_conntrack_ftp, " 
[FONT=inherit][/FONT]$MODPROBE nf_conntrack_ftp
[FONT=inherit][/FONT]echo -en "nf_conntrack_irc, " 
[FONT=inherit][/FONT]$MODPROBE nf_conntrack_irc
[FONT=inherit][/FONT]echo -en "iptable_nat, "
[FONT=inherit][/FONT]$MODPROBE iptable_nat
[FONT=inherit][/FONT]echo -en "nf_nat_ftp, "
[FONT=inherit][/FONT]$MODPROBE nf_nat_ftp
[FONT=inherit][/FONT]echo "----------------------------------------------------------------------"
[FONT=inherit][/FONT]echo -e "   Done loading modules.\n"
[FONT=inherit][/FONT]echo "   Enabling forwarding.."
[FONT=inherit][/FONT]echo "1" > /proc/sys/net/ipv4/ip_forward
[FONT=inherit][/FONT]echo "   Enabling DynamicAddr.."
[FONT=inherit][/FONT]echo "1" > /proc/sys/net/ipv4/ip_dynaddr 
[FONT=inherit][/FONT]echo "   Clearing any existing rules and setting default policy.."
[FONT=inherit][/FONT]
[FONT=inherit][/FONT]iptables-restore <<-EOF
[FONT=inherit][/FONT]*nat
[FONT=inherit][/FONT]-A POSTROUTING -o "$EXTIF" -j MASQUERADE
[FONT=inherit][/FONT]COMMIT
[FONT=inherit][/FONT]*filter
[FONT=inherit][/FONT]:INPUT ACCEPT [0:0]
[FONT=inherit][/FONT]:FORWARD DROP [0:0]
[FONT=inherit][/FONT]:OUTPUT ACCEPT [0:0]
[FONT=inherit][/FONT]-A FORWARD -i "$EXTIF" -o "$INTIF" -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT 
[FONT=inherit][/FONT]-A FORWARD -i "$INTIF" -o "$EXTIF" -j ACCEPT
[FONT=inherit][/FONT]-A FORWARD -j LOG
[FONT=inherit][/FONT]COMMIT
[FONT=inherit][/FONT]EOF
[FONT=inherit][/FONT]
[FONT=inherit][/FONT]echo -e "\nrc.firewall-iptables v$FWVER done.\n"
[/LIST]

```

Any insight would be greatly appreciated. 

Thanks

---

