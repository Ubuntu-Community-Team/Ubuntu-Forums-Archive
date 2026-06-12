---
title: "newbie trying to set up DNS"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by Random Bob on 2009-02-12
I've installed and configured bind + dnsutils but I'm unable to connect to my webserver.  I registered a domain name ([www.terulia.com](www.terulia.com)) with godaddy.com and I have the DNS servers set as NS1.TERULIA.COM and NS2.TERULIA.COM.  I've set up apache and everything on the server, so I can connect to it using the IP address, but when I type [www.terulia.com](www.terulia.com), it won't direct me to the computer.  I have no experience in setting up DNS, and I was wondering if someone could tell me what I did wrong?  I copied down all of the changes/commands step by step in case I need to repeat them later, and I've listed them below:


```
sudo apt-get install bind9 dnsutils
sudo nano /etc/bind/named.conf/local
	add the following lines:
		zone "terulia.com" {
		type master;
		file "/etc/bind/zones/terulia.com.db";
		};
		# replace with network address in reverse notation
		# e.g 192.168.2.x => 2.168.192
		zone "2.168.192.in-addr.arpa" {
		type master;
		file "/etc/bind/zones/rev.2.168.192.in-addr.arpa";
		};
	save
sudo nano /etc/bind/named.conf/options
	uncomment/edit:
		forwarders {
			IP for ISP's DNS server
		};
	save
sudo mkdir /etc/bind/zones
sudo nano /etc/bind/zones/terulia.com.db
	add lines:
		terulia.com. IN SOA ns1.terulia.com. admin.terulia.com. (
		2007031001
		28800
		3600
		604800
		38400
		)
		terulia.com. IN NS ns1.terulia.com.
		terulia.com. IN MX 10 mail.terulia.com.
		www IN A 192.168.2.5
		mta IN A 192.168.2.5
		ns1 IN A 192.168.2.5
	save
sudo nano /etc/bind/zones/rev.2.168.192.in-addr.arpa
	for "# IN PTR", # = address of the DNS server
	e.g. 5 if 192.168.2.5
	add lines:
		@ IN SOA ns1.terulia.com. admin.terulia.com. (
		2007031001;
		28800;
		604800;
		604800;
		86400
		)
		IN NS ns1.terulia.com.
		5 IN PTR terulia.com
	save
sudo /etc/init.d/bind9 restart
sudo nano /etc/resolv.conf
	edit:
		search terulia.com
		nameserver 192.168.2.5
	save
```

---

### Post by ibuclaw on 2009-02-12
```
sudo nano /etc/resolv.conf
```

And put in the DNS server IP address there as so:
```
nameserver **208.67.222.222**
nameserver **208.67.220.220**

```
But use the addresses of your nameserver, rather than the ones above.

Or, you can set it up with the Network Manager Applet.
Right-Click the applet in the notification area and select "**Edit Connections**", locate your active connection in the tabs, highlight and select "**Edit**".
Then select the "**IPv4 Settings** tab then set the Mothod to either "**Automatic (DHCP) addresses only**" or "**Manual**", depending on whether or not you have are connected to a Router or DHCP server.

Then add the IP Addresses of the DNS server/s in the "**DNS Servers**" text box.

[EDIT]
Also, have you restarted the networking daemon?

```
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start

```

Regards
Iain

---

### Post by Random Bob on 2009-02-13
So I edited resolv.conf thus:

```

search terulia.com

nameserver 68.87.74.162
nameserver 68.87.68.162

```

and restarted the networking daemon like you said.
It didn't work, so I checked the Network Manager Applet and tried to make the changes you recommended.
That didn't work, so I checked resolv.conf again, and it had changed.
So I edited resolv.conf (as shown above) and restarted the computer.

After rebooting, it still wasn't working, so I checked resolv.conf
It had changed yet again, and now it says:

```

search Dynex

nameserver 192.168.2.1
nameserver 192.168.2.1
nameserver 68.87.74.162

```

I am using a Dynex router, and 68.87.74.162 and 68.87.68.162 are the DNS servers according to the router setup.
Could resolv.conf resetting be part of the problem?
It's still not able to connect at all using DNS.
(but I can connect directly using the IP address)

---

### Post by Random Bob on 2009-02-15
It's still not working.

I used the online diagnostic at [http://www.ip-plus.net/tools/dns_check_set.en.html]("http://www.ip-plus.net/tools/dns_check_set.en.html") and it gave me the feedback shown below.

I have no idea what to make of this or what to change.
Also I started getting Gnome settings daemon startup errors after making the changes mentioned by tinivole.
Can anyone help me get this thing set up and working?  Thanks.

```

Check if the server "xx.xx.xxx.xxx" is configured for "terulia.com" ... ok.

Check SOA Record ...
Server: c-xx-xx-xxx-xxx.hsd1.fl.comcast.net
Address: xx.xx.xxx.xxx

Query about terulia.com for record types SOA
Trying terulia.com ...
terulia.com         	86400	IN	SOA	ns1.terulia.com admin.terulia.com (
			2007031001	;serial (version)
			10800	;refresh period (3 hours)
			3600	;retry interval (1 hour)
			604800	;expire time (1 week)
			86400	;default ttl (1 day)
SOA Record ok

Check NS Records ...
Server: c-xx-xx-xxx-xxx.hsd1.fl.comcast.net
Address: xx.xx.xxx.xxx

Query about terulia.com for record types NS
Trying terulia.com ...
Query done, 1 answer, authoritative status: no error
terulia.com         	86400	IN	NS	ns1.terulia.com
ns1.terulia.com is primary nameserver
Additional information:
ns1.terulia.com     	86400	IN	A	192.168.2.5
Found IP address "192.168.2.5" for server "ns1.terulia.com"
*** WARNING *** failed reverse lookup for "192.168.2.5"
*** WARNING *** 192.168.2.5  PTR record not found.
*** WARNING *** It's recommended to have reverse lookup for your nameservers
*** ERROR *** At least two nameservers are required.
*** ERROR *** The IP address "xx.xx.xxx.xxx" you specified as a nameserver address
*** ERROR *** is not a valid nameserver for "terulia.com" or the NS record is missing

Check SOA Record for Consistency on all Servers  ...
*** WARNING ***  !!! terulia.com has only one nameserver ns1.terulia.com

terulia.com         	NS	ns1.terulia.com
*** ERROR *** Nameserver ns1.terulia.com not responding

*** ERROR *** terulia.com SOA record not found at ns1.terulia.com, try again


```

---

