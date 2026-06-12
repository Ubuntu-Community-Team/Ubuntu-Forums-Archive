---
title: "Can't do internet connection sharing through a router"
date: 2006-09-11
forum: Networking &amp; Wireless
---

### Post by ssalman on 2006-09-11
I’m trying to setup a firewall/filtering PC for a local network, but I hit a wall being not able to share the internet connection through my router. Here is the setup: I have a PC with Ubuntu installed and 2 NICs. I’m using the below commands to enable NAT (from [this ]("https://help.ubuntu.com/community/InternetConnectionSharing")wiki page), and I have installed and configured dnsmasq to do the DNS and DHCP.
   
```
$sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
$sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward" 
```  
Now this setup works great when I directly connect another PC to my firewall/filtering PC using a crossover cable. But when I connect my router instead of the PC I can’t get to the internet, here is what I tried so far:
   
  -Connecting the firewall/filtering PC to the router using a crossover cable to the internet/wan port on the router. This gave me a connected light on the router, but still no internet connection in the router setup screens ([http://192.168.2.1]("http://192.168.2.1/")) or through the router using other PCs. I could not ping PCs across the router either.
  

-Connecting the firewall/filtering PC to the router using a regular cable to one of the LAN ports on the router. This did not give me a connection light on the router, however I was able to ping both PC across the router. But still with no connection to the internet.
   
  I know my problem lays between the router and my firewall/filtering PC, what am I doing wrong?
   
  Thanks for all your help in advance.

---

### Post by tbonius on 2006-09-11
there seems to be a lot of questions revolving around making Ubuntu a firewall/router/NAT for other computers to access the internet though it.

You need to know some basics about networking first.  You computer connected directly to your DSL/Cable modem most likely needs a dynamic IP address.  Configure whichever interface you would like to be your "External" interface directly to the DSL/Cable modem and then reboot the modem.  Temporarily disable your "Internal" interface so that we can JUST test direct connectivity.  Enable DHCP on your "External" interface and renew your DHCP lease.  DO you get an IP address?

ifconfig -a

If you did not.. then either you have the incorrect interface connected or your ISP mught do MAC addredd filtering.. only allowing one computer to access the network.

If you did get an address.. try opening a web page or pinging a well know internet site like [www.yahoo.com](www.yahoo.com)

Now we need to configure the "Internel" interface.  Configure this interface with a private range IP address (such as 192.168.0.1).  Be sure and give it a subnet mask (255.255.255.0) but DO NOT give it a default gateway address.

Next you would indded enable IP forwarding for the kernel.  IP forwarding is enabled by simply adding the following line to /etc/sysctl.conf:

```
#Enable packet forwarding
net.ipv4.ip_forward = 1
```

**Configuring a ruleset**

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
$IPTABLES -A FORWARD -i $EXTIF -d 192.168.0.5 -p tcp --dport 25 -j ACCEPT
$IPTABLES -t nat -A PREROUTING -i $EXTIF -p tcp --dport 25 -j DNAT --to-destination 192.168.0.5:25

```

This script assumes that we are using eth0 for our external interface and eth1 for the internal interface. If you have a different setup then adjust the script accordingly and change the EXTIF and INTIF values as well as the redirection rules to match whatever ports you want to forward to whatever internal computers.

Be sure and make this script executable:

```
sudo chmod +X /sur/local/sbin/firewall.sh
```

We now need to create an IPtables startup script.  In /etc/init.d create a file called iptables edit it to look like the following:

```
#!/bin/sh
#
#This is a ubuntu adapted iptables script from gentoo
#(http://www.gentoo.org) which was originally distributed
# under the terms of the GNU General Public License v2
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
start-stop-daemon --start --quiet --exec /sbin/iptables-restore -- ${SAVE_RESTOR
E_OPTIONS} < ${IPTABLES_SAVE}
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
start-stop-daemon --stop --quiet --pidfile /var/run/iptables.pid --exec /sbin/ip
tables
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

Now go ahead and make the file executable:
```

sudo chmod +x /etc/init.d/iptables

```
And make it startup when the system reboots:
```

sudo update-rc.d iptables default

```

We now need to start the IPTables service so that we can load this ruleset:

```
sudo /etc/init.d/iptables start
* Loading iptables state and starting firewall...	[ ok ]
* Restoring iptables ruleset    			[ ok ]

```

Now simply run the firewall.sh script to load the ruleset and test it out. 

```
sudo /usr/local/sbin/firewall.sh
```

When you have verified the rules are woking and traffic is being routed correctly, you can permanently save the rules by running the following command:

```

sudo /etc/init.d/iptables save
* Saving iptables state...  				[ ok ]

```

Again, before blindly using the ruleset demostrated here, keep in mind that this is not the most secure ruleset. In this example we are allowing all traffic passed out. Ideally, we would filter outgoing traffic as well. From here you need to statically configure your internal computers with IP addresses.

Start by using something like 192.168.0.10 with a subnet mask of 255.255.255.0 and a default gateway of 192.168.0.1.  Also be sure and configure the same DNS servers that the firewall is using (check /etc/resolv.conf to get these IP addresses).  From here you should get internet access from your laptop or whatever other "Internal" computers you have.

If you want your Ubuntu computer to also act as a DHCP server.. handing out dynamic addresses to your "Internal" computers.. then you can do that as well.  Post back and let me know if you need help doing this.

T

---

### Post by ssalman on 2006-09-11
Thanks tbonius!, That was some detailed help :D. I was going in the same direction as you wrote, a little less detailed just to get the basic job done, but very similar. There are few things that I will incorporate into my final script from your post, Thanks!...

Still, I think you may missunderstod my post and thought that I'm not able to do the basic connection sharing... I am able to share my connection with a nother PC with iptables masquerade, dnsmasq, and ip_forward. the problem is that I want to share the connection with a local network of computers through a router, and I can't get the router to distribute my connection... as if my router is not getting the connection sharing that the regular PC was...:confused:

---

### Post by tbonius on 2006-09-11
Your post doesnt make sense to me.  Are you using the Ubuntu computer as your router?  If so.. re read the instructions.. that should work for a whole network of computers.

If you are using a third party router (such as a Linksys or a Netgear) then the setup is straight forward.. that router already provides NAT/firewalling (Internet COnnection Sharing) for you.

T

---

### Post by ssalman on 2006-09-11
Well, I'm actually using my ubuntu box for filtering my internet connection, so it is not my router, it is just the filtering box. I want to connect it to a belkin wireless router that will share the filtered connection with the rest of the local network.  As you see I can't do this with the ubuntu box alone, or the belkin router alone. I have to combine them both to share my filtered connection wirelessly:D

Thanks for your help so far.

---

### Post by tbonius on 2006-09-12
What you are describing is actually two different networks.  Instead, try using the Ubuntu computer as your Main Firewall/NAT router to the internet and then connect your Netgear as JUST a wireless access point (disable the WAN functionality) and do pass through DHCP and such from your Ubuntu computer as the DHCP/DNS server.  You can assign a static IP to the internal IP of the Netgear .. turn on the wireless.. and just plug up the Ubunto computer to one of the ports.  That is what I do with my Linksys.

T

---

### Post by ssalman on 2006-09-12
> **tbonius said:**
> connect your Netgear as JUST a wireless access point (disable the WAN functionality)

Great, I will give it a try this week and report back, Thanks for all your help! :)

---

### Post by ssalman on 2006-09-18
Well, I tried many times to setup my router as an access point, but I think there is a bug in the router firmware as it is not saving the changes. I have a Belkin F5D6231-4_V2 wireless router, and I have sent an email to the customer support 4 days ago, and I'm still waiting for their reply.

But someone on a different forum suggested that I use a proxy server, so I installed tinyproxy, and after tinkering with its configuration files, I’m now able to share my filtered internet connection through the router :) I will play with it some more to figure out all what I need, but I think I have got my self a solution. Thanks for your help tbonius nevertheless.

Still I'm having a problem: because I have two NICs on my proxy PC, two servers answer DHCP requests: the DSL modem, and my router, and they overwrite each others DNS and routing table info. :( so my internet connection get messed up.

I tried to setup /etc/iftab so that I have the eth1 and eth2 fixed and not switching around every boot (which worked so far) and then setup /etc/network/interfaces so that only my modem facing NIC will use DHCP, while the router facing NIC uses static IP setup, still it didn’t work, I had to disconnect my router and lunch dhclient and reconnect my router when finished in order to fix the internet connection. Another reason I want a static ip on the router facing NIC is that I don't want to change my browser settings every time the IP address change.

What can I do to fix this issue?


Thanks

---

### Post by ssalman on 2006-09-19
[FONT=Verdana]Found the problem... it was the DNS settings being overwritten by the last NIC being brought up, so I switched the eth numbers in iftab where the NIC facing the DSL modem (the one with DHCP) being last, and the one with static IP (the NIC facing the router) being first, and so the modem will dictate the DNS settings… works like a charm.


Still nothing from belkin, I'll give them a call today. Now I can't protect my wireless signal with WEP, because of this bug.

-- Edit : Update --

I figured out why my router won't save the settings... I was using firefox, and when I use internet explorer it worked fine... what a [/FONT][FONT=Verdana]surprise[/FONT][FONT=Verdana]!!![-X SURPRISE, I tell you. ;)
[/FONT]

---

