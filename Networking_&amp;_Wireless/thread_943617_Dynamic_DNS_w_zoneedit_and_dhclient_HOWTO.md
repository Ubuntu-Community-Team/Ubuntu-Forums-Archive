---
title: "Dynamic DNS w/ zoneedit and dhclient HOWTO"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by jeremynd01 on 2008-10-10
I just successfully setup dynamic dns (dyndns) using the free DNS service from [www.zoneedit.com](www.zoneedit.com) without the need for an external client (ddclient, no-ip, or similar), and wanted to share the config with you and the rest of the world.

Provisos:
1) You have a linux box (gateway/firewall/etc) that receives your internet routeable dynamic IP address (i.e. you're not behind a router appliance or NAT device).  For me, this means my DSL modem is configured to show the public IP on the ethernet port (aka a "visible" but not "bridged" mode.  More on bridged later...).

2) You have gone to [www.zoneedit.com](www.zoneedit.com) and signed up for an account, and have the login/pass info on hand.

3) You have registered for a domain name (i.e. from [www.godaddy.com](www.godaddy.com) or another registrar) and have entered the DNS server information that you received in (2).


Provided that, you need only add a file in the /etc/dhpc3/dhclient-exit-hooks.d/ directory that has the following line:

```
wget -O - --http-user=username --http-passwd=password 'http://dynamic.zoneedit.com/auth/dynamic.html?host=www.mydomain.com'
```


(taken from [http://www.zoneedit.com/doc/dynamic.html?](http://www.zoneedit.com/doc/dynamic.html?))
You'll want to substitute 'username,' 'password,' and 'www.mydomain.com' with the login info for you zoneedit.com account and your domain.

According to dhclient man page, whenever the DHCP client has to get a new IP, it'll run the scripts in /etc/dhpc3/dhclient-exit-hooks.d/ from the /sbin/dhclient-script tool.  This is why there is no #!/bin/sh in the script - it is sourced from another program.  Hence, no need for an external dynamic dns client: dhclient already has the function built in.

Caveat: this uses wget to send the username and password in PLAIN TEXT, so is pretty insecure.  Though undocumented by zoneedit.com, the following seemed to work using an SSL connection (use it in place of the wget command above):

```
wget --no-check-certificate -O - --http-user=username --http-passwd=password 'https://dynamic.zoneedit.com/auth/dynamic.html?host=www.mydomain.com'
```

The --no-check-certificate switch is used to ignore an error that the certificate name (issued to dnsvr.com) does not match the FQDN (dynamic.zoneedit.com).  I assume it's legit.

Finally, a note on bridging: My DSL modem (Motorola Netopia 2210 from AT&T) allows three modes: PPPoE on the modem and private (192.168.x.x) IP on the LAN, PPPoE on modem and public (DHCP assigned) IP on the LAN, or Bridged mode, where PPPoE must be setup on the gateway.  I use the second option.  If you use RP-PPPoE on your box with a bridge modem, then I don't see why this won't work (dhclient still has to get the IP address), but I haven't tested it.  If it doesn't work, then (Once upon a time, with Redhat7/8/9,) it should be possible to use RP-PPPoE to do a very similar thing with a script that ran after the ppp0 address changed.

Happy serving!

---

