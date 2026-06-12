---
title: "Can't start Ubuntu after install a new router.  DHCP / runlevel problem"
date: 2019-11-06
forum: Networking &amp; Wireless
---

### Post by virilo on 2019-11-06
I changed my router and now I can't start my Ubuntu.  It seems to be a DHCP problem.  

First of all, I can't understand the OS not being able to startup without internet connection.
I must be something that I added to the bootstrap in the wrong runlevel, and it's requiring Internet connection to continue bootstrap.

I removed two homebrew scripts during the bootstrap that caused a infinite loop due to the lack of Internet access.

Now, it still hangs saying nothing.  Perhaps it's trying to mount a smb folder in the wrong runlevel, or something.

I started the root console and journal -b -1 says only this:

```
	-- Logs begin at mié 2019-11-06 06:50:02 CET, end at mié 2019-11-06 07:07:22 CET. --
	nov 06 06:50:02 ComputerName dnsmasq[1575]: started, version 2.75 cache disabled
	nov 06 06:50:02 ComputerName dnsmasq[1575]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth DNSSEC loop-detect inotify
	nov 06 06:50:02 ComputerName dnsmasq[1575]: DBus support enabled: connected to system bus
	nov 06 06:50:02 ComputerName dnsmasq[1575]: warning: no upstream servers configured
	nov 06 06:50:02 ComputerName dnsmasq[1575]: setting upstream servers from DBus
	nov 06 06:50:02 ComputerName dnsmasq[1575]: using nameserver 62.81.16.213#53(via enp5s0)
	nov 06 06:50:02 ComputerName dnsmasq[1575]: using nameserver 62.81.29.254#53(via enp5s0)
```

And this is my dhclient.conf:

	option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

```
	send host-name = gethostname();
	request subnet-mask, broadcast-address, time-offset, routers,
		domain-name, domain-name-servers, domain-search, host-name,
		dhcp6.name-servers, dhcp6.domain-search, dhcp6.fqdn, dhcp6.sntp-servers,
		netbios-name-servers, netbios-scope, interface-mtu,
		rfc3442-classless-static-routes, ntp-servers;

	timeout 300;
```

I'd like my Ubuntu to start without Internet connection.  Or as a workaround, to solve the problem with the router.

In the router side, I change the net to 192.168.1.xxx, in order my computer can get its static IP.
The router can see the computer, and says it has given my computer its static IP.

Any help will be wellcome

---

### Post by virilo on 2019-11-06
After configuring dhcp and boot using noveau.modeset=0, the problem persists, but the output is more verbose.

I shared journalctl -b-1 output here: [https://raw.githubusercontent.com/virilo/kaggle-forums/master/askubuntu/hangs-during-bootstrap.txt](https://raw.githubusercontent.com/virilo/kaggle-forums/master/askubuntu/hangs-during-bootstrap.txt)

---

