---
title: "Firewall Failed to Start"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by ljmagyar on 2006-09-07
:confused: Ok, so I've searched and read and haven't found a head-slapper of a solution to my problem.  Here's hoping for some help.

System config:

DSL Modem -> eth0 ->Ubuntu 6.06 Dapper Drake w/LAMP, DHCP, & Firestarter ->eth1 -> Netgear 24 port hub -> client X86 machines

I can get OUT from the server to the WWW but when i try to start the LAN / Firewall I get the 'Firewall Failed to Start - eth1 not ready' error.

I want to have a few static IPs and a range of dynamic IPs for guests (I often host LAN gaming parties).  I had been using FREESCO for my NAT/Router but needed a bit more complexity for a different task.

I would also like to be able to use eth2 for a different subnet on the same server.

I *think* I configured things correctly.  Eth0 is using the gateway, static IP, and DNS provided by my ISP - and is working fine.  I am trying to use 192.168.101.1 for the IP of eth1 and 192.168.110.1 for eth2.  The DHCP range for both is 192.168.XXX.101 192.168.XXX.124.  These have been set in the /etc/dhcp.conf file

Which conf files do I need to be scanning for problems?  Any help resolving (sic) my problems would be greatly appreciated.

TIA
Lou

---

### Post by tbonius on 2006-09-07
OK, so your internal NICS (eth1 and eth2) are assigned dynamic addresses as well?  Your dhcp.conf is for a dhcp client.  Do you mean your dhcpd.conf for dhcp3-server?  I assume you want to be a dhcp server for those two LANs.

Make sure each internal interface has a static address and netmask.. but NO default gateway.  Only the external interface (eth0) should get a default gateway from your ISP.

Next you can configure your firewall:

Im not very familiar with Firestarter.. but IPtables should work fine as is.. you just need some sort of config file and a startup script for IPtables. (as well as a IPv4 forwarding on the interfaces)

IP forwarding is enabled by simply adding the following line to /etc/sysctl.conf:

```
#Enable packet forwarding
net.ipv4.ip_forward = 1
```

Now you need to configure a firewall ruleset

The following example shell script creates a basic ruleset that allows all traffic out from an internal network and only a couple of ports inbound. This script should be created and saved in a convenient and accessible place like /usr/local/sbin. Name this script whatever you would like to call it, like maybe firewall.sh

```
#!/bin/sh
IPTABLES='/sbin/iptables'

# Set interface values
EXTIF='eth0'
INTIF='eth1'

# enable ip forwarding in the kernel
/bin/echo 1 > /proc/sys/net/ipv4/ip_forward

# flush rules and delete chains
$IPTABLES -F
$IPTABLES -X

#Enable masquerading to allow LAN internet access
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

#Forward LAN traffic from LAN $INTIF to Internet $EXTIF
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -m state --state NEW,ESTABLISHED -j ACCEPT

#Allowing access to the SSH server"
$IPTABLES -A INPUT --protocol tcp --dport 22 -j ACCEPT

#Allowing access to the HTTP server"
$IPTABLES -A INPUT --protocol tcp --dport 80 -j ACCEPT

# block out all other Internet access on $EXTIF
$IPTABLES -A INPUT -i $EXTIF -m state --state NEW,INVALID -j DROP
$IPTABLES -A FORWARD -i $EXTIF -m state --state NEW,INVALID -j DROP

#Redirect TCP port 25 to another internal computer
$IPTABLES -A FORWARD -i $EXTIF -d 10.0.0.5 -p tcp --dport 25 -j ACCEPT
$IPTABLES -t nat -A PREROUTING -i $EXTIF -p tcp --dport 25 -j DNAT --to-destination 10.0.0.6:25
```


This script assumes that we are using eth0 for our external interface and eth1 for the internal interface. If you have a different setup then adjust the script accordingly and change the EXTIF and INTIF values (and even add addition INTIF values for other interfaces..  INTIF-0  INTIF-1.. etc..)

Once this is done we can create an iptables startup script in /etc/init.d to look like the following:

```

#!/bin/sh
#
#This is a ubuntu adapted iptables script from gentoo
#(http://www.gentoo.org) which was originally distributed
#under the terms of the GNU General Public License v2
#and was Copyrighted 1999-2004 by the Gentoo Foundation
#
#This adapted version was intended for and ad-hoc personal
#situation and as such no warranty is provided.

IPTABLES_SAVE="/etc/default/iptables-rules"
SAVE_RESTORE_OPTIONS="-c"
SAVE_ON_STOP="yes"

checkrules() {
if [ ! -f ${IPTABLES_SAVE} ]
then
echo "Not starting iptables. First create some rules then run"
echo "\"/etc/init.d/iptables save\""
return 1
fi
}

save() {
echo "Saving iptables state"
/sbin/iptables-save ${SAVE_RESTORE_OPTIONS} > ${IPTABLES_SAVE}
}

start(){
checkrules || return 1
echo "Loading iptables state and starting firewall"
echo -n "Restoring iptables ruleset"
start-stop-daemon --start --quiet --exec /sbin/iptables-restore -- ${SAVE_RESTORE_OPTIONS} < ${IPTABLES_SAVE}
}

case "$1" in
save)
save
echo "."
;;

start)
start
echo "."
;;
stop)
if [ "${SAVE_ON_STOP}" = "yes" ]; then
save || exit 1
fi
echo -n "Stopping firewall"
for a in `cat /proc/net/ip_tables_names`; do
/sbin/iptables -F -t $a
/sbin/iptables -X -t $a

if [ $a == nat ]; then
/sbin/iptables -t nat -P PREROUTING ACCEPT
/sbin/iptables -t nat -P POSTROUTING ACCEPT
/sbin/iptables -t nat -P OUTPUT ACCEPT
elif [ $a == mangle ]; then
/sbin/iptables -t mangle -P PREROUTING ACCEPT
/sbin/iptables -t mangle -P INPUT ACCEPT
/sbin/iptables -t mangle -P FORWARD ACCEPT
/sbin/iptables -t mangle -P OUTPUT ACCEPT
/sbin/iptables -t mangle -P POSTROUTING ACCEPT
elif [ $a == filter ]; then
/sbin/iptables -t filter -P INPUT ACCEPT
/sbin/iptables -t filter -P FORWARD ACCEPT
/sbin/iptables -t filter -P OUTPUT ACCEPT
fi
done
start-stop-daemon --stop --quiet --pidfile /var/run/iptables.pid --exec /sbin/iptables
echo "."
;;

restart)
echo -n "Flushing firewall"
for a in `cat /proc/net/ip_tables_names`; do
/sbin/iptables -F -t $a
/sbin/iptables -X -t $a
done;
start
echo "."
;;
*)
echo "Usage: /etc/init.d/iptables {start|stop|restart|save}" >&2
exit 1
;;
esac

exit 0

```

Save this file.. and make it executable

```
user@host# sudo chmod +x /etc/init.d/iptables
```

Then make sure it starts every time Linux boots:

```
user@host# sudo update-rc.d iptables defaults
```

We now need to start the IPTables service so that we can load this ruleset:

```

user@host # sudo /etc/init.d/iptables start
* Loading iptables state and starting firewall...	[ ok ]
* Restoring iptables ruleset    			[ ok ]

```

Now simply run the firewall.sh script to load the ruleset and test it out. When you have verified the rules are woking and traffic is being routed correctly, you can permanently save the rules by running the following command:

```
user@host # sudo /etc/init.d/iptables save
* Saving iptables state...  				[ ok ]

```

Again, before blindly using the ruleset demostrated here, keep in mind that this is not the most secure ruleset. In this example we are allowing all traffic passed out. Ideally, we would filter outgoing traffic as well. 

As far as DHCP goes.. you would need to setup the "dhcp3-server" package.  

Hope this helps.. and if you need any additional assistance with DHCP server.. lemme know.

T

---

### Post by ljmagyar on 2006-09-07
Wow T, that is a lot of great info and should certainly get me going where i need to go.  I will digest and incorporate it.

Regarding my client-side ethernet cards, my intention is this:

eth1 is seen by the server as 192.168.101.1
eth2 as 192.168.110.1

both provide a combo of static & DHCP addresses to the 24-port hubs  each is connected to.  I want some fixed and some dynamic IPs from eth1 & eth2.  The DHCP range is inconsequential, but i would like SOME fixed IPs for my resident machines. (I have 6 on my network - 4 on one and 2 on the other hub.)

ALL clients need access out.  I typically only open a few ports for gaming hosts.

My FreeSCO box was setup to perform in this manner, and worked like a charm.  (in fact, I am writing this using it presently) However, i needed features (that FreeSCO has, but are cumbesome) to run a newsletter server.  the newsletter script requires MySQL and PHP, which i installed on (this) server, but could not get working properly.

I am tenatious, and will work on the Ubuntu config until it can replace and exceed the FreeSCO servers capabilities. And to that end, I thank you for your assistance!

Regards,
Lou

---

### Post by tbonius on 2006-09-07
Not a problem..

This sounds like a simple enough setup.  Let me know if you need any additional help in getting it going.  I recommend finding a few articles on setting up your dhcpd.conf to handle the leases.. its pretty straight forward.  I hope the IPtables rules made sense to you.

T

---

### Post by ljmagyar on 2006-09-08
I havent had the opportunity to sit down and mess with it since Wednesday night.  the IP tables look like i should be able to figure things out fairly well.

if i understand, the following code:
# Set interface values
EXTIF='eth0'
INTIF='eth1'

should read (for my application):
# Set interface values
EXTIF='eth0'
INTIF-0='eth1'
INTIF-1='eth2'

would i need to edit this at all?:

#Forward LAN traffic from LAN $INTIF to Internet $EXTIF
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -m state --state NEW,ESTABLISHED -j ACCEPT

for example, should it be?:
#Forward LAN traffic from LAN $INTIF to Internet $EXTIF
$IPTABLES -A FORWARD -i $INTIF-0 -o $EXTIF -m state --state NEW,ESTABLISHED -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF-1 -o $EXTIF -m state --state NEW,ESTABLISHED -j ACCEPT

(I dont think so, but i thought i had better ask)

It is indeed a simple config, which is why i was so stumped that the 'firewall failed to start' because the 'eth1 was not ready'.

I will hopefully get things set up this weekend and give your advice a shot.  thanks for taking the time to write so thorough a response.  i really appreciate it.

---

### Post by tbonius on 2006-09-08
Yes you would need to edit the iptables rules exactly how you posted them.

T

---

### Post by ljmagyar on 2006-09-10
well, i'm not getting anywhere.  i setup the iptables how you said, making the eidts as needed, but i still can't get any NAT to work on clients.  the order of doing things you mentioned needed a bit of rearranging, but everything appeared to work.

what can i do to diagnose the problem?  what files do i need to look in for proper config?  i am really getting bummed that this isnt working.  everything SHOULD work, but it isnt.  the eth cards are all working and recognized, the whole thing looks right... but it just wont work!!!

My clients can ping the server, and the server can ping the clients, but the clients can not access the WWW at all.  I am at a loss as to what I can do to rectify the situation.

---

### Post by tbonius on 2006-09-11
Make sure you are doing port forwarding with the sysctl option specified earlier..  Also.. is your Ubuntu server able to ping Internet sites?  Double check its IP address settings.

When you run the firewall.sh script.. does it spit back any errors?

T

---

### Post by ljmagyar on 2006-09-11
i am browsing the web with the server machine right now.

ping from server 192.168.0.1 (eth1) works to client at 192.168.0.28 (static IP on laptop next to server)
ping from laptop @ 192.168.0.28 works to server 192.168.0.1 (eth1)

ping from 192.168.0.28 to eth0 does NOT work
ping from server to 'gateway' works
ping from 192.168.0.28 to 'external gateway' does NOT work

the ip forwarding in sysctl is uncommented for both ipv4 and ipv6

i read somewhere about the loopback should be removed... should i remove it? did i read wrong?

when i ran the firewall.sh scrip there were no errors, but i DID have to 'create rules' in a different order than you specified in this thread.  perhaps this is the issue?

---

### Post by ljmagyar on 2006-09-11
perhaps this will help a bit:

x@x:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:xxx.xxx.xxx.xxx  Bcast:xxx.xxx.xxx.255  Mask:255.255.255.0
          inet6 addr: xxxx::xxx:xxxx:xxxx:b509/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2231 errors:2 dropped:0 overruns:0 frame:4
          TX packets:2125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1424375 (1.3 MiB)  TX bytes:304360 (297.2 KiB)
          Interrupt:11 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: xxxx::xxx:xxxx:xxxx:3147/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:783 errors:0 dropped:0 overruns:0 frame:0
          TX packets:583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:80444 (78.5 KiB)  TX bytes:134203 (131.0 KiB)
          Interrupt:5 Base address:0xa400

eth2      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0x6800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:262 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:98292 (95.9 KiB)  TX bytes:98292 (95.9 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by tbonius on 2006-09-12
Disable IPv6 and make rules to allow the subnets to talk to each other.  Also.. try to ping the external IP of your Ubuntu server from a computer on each subnet.

T

---

