---
title: "Setting up PPTP VPN connection in konsole."
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by Mikorist on 2008-11-26
Install PPTP Client from the Debian Project:
```
sudo apt-get install pptp-linux
```

make pptpvpn   file:
```
#!/bin/bash
function routeadd {
   route add -host 61.xxx.xxx.xxx dev ppp0
   route add -host 62.xxx.xxx.xxx dev ppp0
   route add -host 63.xxx.xxx.xxx dev ppp0
}
function makepptp {
   echo pty \"pptp VPN.SERVER.COM --nolaunchpppd\" >> /etc/ppp/peers/pptpvpn;
   echo remotename PPTP >> /etc/ppp/peers/pptpvpn;
   echo require-mppe-128 >> /etc/ppp/peers/pptpvpn;
   echo file /etc/ppp/options.pptp >> /etc/ppp/peers/pptpvpn;
   echo ipparam pptpvpn >> /etc/ppp/peers/pptpvpn;
pppd call pptpvpn &
}
if [ -a /etc/ppp/chap-secrets ];
		then
		rm /etc/ppp/chap-secrets
	echo $1 PPTP $2 '*' >> /etc/ppp/chap-secrets;
else
	echo $1 PPTP $2 '*' >> /etc/ppp/chap-secrets;
fi

if [ -e /etc/ppp/peers/pptpvpn ];
	then
	rm /etc/ppp/peers/pptpvpn;
	echo name $1 >> /etc/ppp/peers/pptpvpn;
	makepptp;
	sleep 8;
	routeadd;
else
	echo name $1 >> /etc/ppp/peers/pptpvpn;	
	makepptp;
	sleep 8;
	routeadd;
fi
```
Where,
pty \"pptp VPN.SERVER.COM --nolaunchpppd\"
Specifies that the command script is to be used to communicate rather than a specific terminal device. In this case we are using pptp client to establishes the client side of a Virtual Private Network (VPN) using the Point-to-Point Tunneling Protocol (PPTP). 
VPN.SERVER.COM  is host name (or IP address) for the VPN server

route add -host 63.xxx.xxx.xxx dev ppp0 - this will tell which hosts are on the other side of tunnel. (host name or IP address)

Close and save the file. 
```
chmod +x pptpvpn
```

```
sudo ./pptpvpn username password
```

If everything is went correctly you should be online and ppp0 should be up. Remote server will assign IP address and other routing information

Disconnect PPTP server vpn connection
Simply kill pppd service, enter:
```
killall pppd
```

it will work on any distribution, its just a matter of 
pptp package you will have to install..

---

### Post by redpanthera on 2009-03-07
-

---

### Post by redpanthera on 2009-03-07
-

---

### Post by onegreenparker on 2009-03-09
Anyone tried this?
Don't want to break anything just yet......

---

### Post by purgen on 2009-10-18
Updated original script that works for me:

```

#!/bin/bash
USERNAME=$1
PASSWORD=$2

function routeadd {
        # route to VPN internal network
	route add -net 10.0.0.0 netmask 255.0.0.0 dev ppp0
}

function makesecrets {
	rm /etc/ppp/chap-secrets  > /dev/null 2>&1
	echo $USERNAME PPTP $PASSWORD '*' >> /etc/ppp/chap-secrets
	sudo chmod 600 /etc/ppp/chap-secrets
}

function makepptp {
	peers=/etc/ppp/peers/pptpvpn;
	rm $peers > /dev/null 2>&1
	echo name $USERNAME >> $peers
	echo pty \"pptp VPN.SERVER.COM --nolaunchpppd\" >> $peers
	echo remotename PPTP >> $peers
	echo require-mppe-128 >> $peers
	echo file /etc/ppp/options.pptp >> $peers
	echo ipparam pptpvpn >> $peers
	
        # optional: configure resolver
	resolv=/etc/ppp/resolv/pptpvpn;
	rm $resolv > /dev/null 2>&1
	echo domain LOCAL.DOMAIN >> $resolv
	echo search LOCAL.DOMAIN VPN.INTERNAL.DOMAIN >> $resolv
	echo nameserver 10.X.X.X >> $resolv       # VPN internal DNS
        echo nameserver 192.168.X.X >> $resolv    # local DNS
}


echo "Updating secrets..."
makesecrets;

echo "Connecting..."
makepptp;
pppd call pptpvpn &

echo "Waiting for ppp0..."
i=30
while [ $i -gt 0 ] ; do
	sleep 1
	if ifconfig ppp0 | grep " UP "; then break; fi > /dev/null
	i=$(($i-1))
done

echo "Routing..."
routeadd;


```

---

### Post by cwhisperer on 2011-03-01
> **purgen said:**
> Updated original script that works for me:

```

#!/bin/bash
USERNAME=$1
PASSWORD=$2

function routeadd {
        # route to VPN internal network
	route add -net 10.0.0.0 netmask 255.0.0.0 dev ppp0
}

function makesecrets {
	rm /etc/ppp/chap-secrets  > /dev/null 2>&1
	echo $USERNAME PPTP $PASSWORD '*' >> /etc/ppp/chap-secrets
	sudo chmod 600 /etc/ppp/chap-secrets
}

function makepptp {
	peers=/etc/ppp/peers/pptpvpn;
	rm $peers > /dev/null 2>&1
	echo name $USERNAME >> $peers
	echo pty \"pptp VPN.SERVER.COM --nolaunchpppd\" >> $peers
	echo remotename PPTP >> $peers
	echo require-mppe-128 >> $peers
	echo file /etc/ppp/options.pptp >> $peers
	echo ipparam pptpvpn >> $peers
	
        # optional: configure resolver
	resolv=/etc/ppp/resolv/pptpvpn;
	rm $resolv > /dev/null 2>&1
	echo domain LOCAL.DOMAIN >> $resolv
	echo search LOCAL.DOMAIN VPN.INTERNAL.DOMAIN >> $resolv
	echo nameserver 10.X.X.X >> $resolv       # VPN internal DNS
        echo nameserver 192.168.X.X >> $resolv    # local DNS
}


echo "Updating secrets..."
makesecrets;

echo "Connecting..."
makepptp;
pppd call pptpvpn &

echo "Waiting for ppp0..."
i=30
while [ $i -gt 0 ] ; do
	sleep 1
	if ifconfig ppp0 | grep " UP "; then break; fi > /dev/null
	i=$(($i-1))
done

echo "Routing..."
routeadd;


```

worked allways for me, but on my new laptop I get following error message SIOCADDRT: Network is down and this for each route I add... Any help will be appreciated ;)

---

