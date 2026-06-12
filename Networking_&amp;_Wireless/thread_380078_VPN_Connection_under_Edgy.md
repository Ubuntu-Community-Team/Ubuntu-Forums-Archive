---
title: "VPN Connection under Edgy"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by Schnoid on 2007-03-09
Hi, I'm trying to connect my Ubuntu Edgy laptop to a VPN over a wireless LAN connection.  The instructions I have are to use pptpconfig and enter the relevant settings and then when this is done, the next instructions are for setting up the routing.  

Firstly, is says to put this script in the file /etc/ppp/route-add.local

> #!/bin/csh

set ppproutesave="/etc/ppp/route-del.local"

set server=`ps -ef | grep "pptp: call manager for" | grep -v grep | awk ' { print $12 }'`
if ( $server == "" ) then
	echo "No PPTP Server found"
	exit
endif

route add -host $server gw 172.16.254.254 dev eth1

/bin/rm $ppproutesave > /dev/null
echo route del -host $server gw 172.16.254.254 dev eth1 > $ppproutesave
echo /bin/rm -f $ppproutesave >> $ppproutesave
chmod 755 $ppproutesave

Then the instructions are
>  Make the file executable by running this command...
chmod 700 /etc/ppp/route-add.local

To call this script as the VPN tunnel is created, and hence automatically add the route on connection, it is necessary to edit the /etc/ppp/ip-up file.
Add the following line above the last line (exit 0) of the /etc/ppp/ip-up file.
/etc/ppp/route-add.local

Similarly to delete this route as the tunnel shuts down when you disconnect, add the following line above the last line (exit 0) of the /etc/ppp/ip-down file.
/etc/ppp/route-del.local 

My first problem is that it says to add /etc/ppp/route-add.local above the last line /etc/ppp/ip-up file which should be exit 0.  I can't see this line /etc/ppp/ip-up.

Can anybody help me?

---

