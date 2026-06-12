---
title: "Network DNS settings..."
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by lokeey on 2006-12-12
Hey all, I'm currently using Kubuntu (Edgy) and I'm noticing that my DNS settings change on their own. I have everything set to default, but for some reason it grabs the gateway of my router as the default nameserver. So I set it to sbcglobal nameserver. Then after awhile, not sure how long to be exact, it grabs the gateway. I didn't have this problem with Dapper. Has anyone noticed this as well with Edgy?

---

### Post by dbott67 on 2006-12-12
This is the default action when you use DHCP (and normal when you have a cable/DSL modem).

Are you editing the resolv.conf and it changes back after each re-boot?
```
gksudo gedit /etc/resolv.conf
```

If so, you can modify the dhclient.conf and add the preferred nameservers:
```
sudo gedit /etc/dhcp3/dhclient.conf
```
Look for the section:
```
#prepend domain-name-servers 127.0.0.1;
```
Remove the comment (#) and change it to:
```
prepend domain-name-servers **[COLOR="Red"]ipaddress.of.name.server[/COLOR]**;
```
Then restart the network and check resolv.conf.

-Dave

---

### Post by lokeey on 2006-12-12
Sorry, I meant to say default being DHCP.

---

### Post by lokeey on 2006-12-12
Hey dbott67, thanks for the quick reply. 

[COLOR="RoyalBlue"]Are you editing the resolv.conf and it changes back after each re-boot? [/COLOR]

[COLOR="Red"]Correct![/COLOR]

[COLOR="RoyalBlue"]If so, you can modify the dhclient.conf and add the preferred nameservers:[/COLOR]

[COLOR="Red"]Done![/COLOR]

[COLOR="RoyalBlue"]prepend domain-name-servers sbcglobal.nameserver[/COLOR]

[COLOR="Red"]Done![/COLOR]

I restart my network...

resolv.conf:
nameserver ns1.sbcglobal.net
nameserver ns2.sbcglobal.net
[COLOR="Red"]nameserver my.default.gateway <--- adds it after restarting my network[/COLOR]

---

### Post by dbott67 on 2006-12-12
Most routers have a DNS forwarder built-in that forwards all requests from the local area network to the ISP nameserver.  If you check the status page of your router (where it reveals your public/external IP address, you should see your ISP name server listed).

Here's mine for comparison:
```
dbott@thedrake:~$ cat /etc/resolv.conf
nameserver 192.168.1.1

```

---

### Post by dbott67 on 2006-12-12
> **lokeey said:**
> I restart my network...

resolv.conf:
nameserver ns1.sbcglobal.net
nameserver ns2.sbcglobal.net
[COLOR="Red"]nameserver my.default.gateway <--- adds it after restarting my network[/COLOR]

This looks good to me.  Are you having problems resolving names?  Or do you just want to get rid of it?  There's a hack around here somewhere, I think, but I wouldn't recommend it if everything is working correctly.

-Dave

---

### Post by lokeey on 2006-12-12
Well, for the most part everything works well. I can chat over GAIM and I can stream music over Amarok just fine; but for some reason it does not let me resolve any names. I make the quick change and I'm good to go. Not big deal, but having to go back in there and update my nameserver to sbcglobal is beginning to be a pain.

---

### Post by dbott67 on 2006-12-12
I think if you remove the part highlighted below from **/etc/dhcp3/dhclient.conf**, then it won't request the name server from your router (which is the DHCP server for your network).

```
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, **[COLOR="Red"]domain-name-servers,[/COLOR]** host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
```

Just be sure to backup the file first:
```
sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.conf.bak
```

-Dave

---

### Post by lokeey on 2006-12-12
Hehehe...that's what I was thinking as I was looking at this file. I just wasn't 100% sure. Thanks for clearing that up, though! I'll try that and see if that works.

Thanks again!

---

### Post by lokeey on 2006-12-12
looks like that did the trick! 8)

---

### Post by dbott67 on 2006-12-12
Great!

---

### Post by johnaaronrose on 2007-04-25
Using Feisty (last week's release) on a Dell Inspiron laptop, I previously altered the prepend statement (on the /etc/dhcp3/dhclient.conf file) for the wired ethernet (eth0) connection to show the open OpenDNS IPs (i.e. 208.67.222 & 208.67.220.220) by handy in November 2005 and that worked fine using Swiftfox (I'd previously used the same technique successfully on an older Acer laptop using Edgy with Firefox).

However, as soon as I'd got the wireless connection working, I disabled the wireless connection (using System/Administration/Network and the Connections tab) and I tried to run Swiftfox. I couldn't browse to any web site and so I checked the DNS tab on System/Administration/Network. And there were no entries other than 0.0.0.0. By the way, the router I'm using doesn't have the DNS IPs storable in it. When I put the appropriate entries in and saved, web sites could be browsed. So Feisty appears to clear DNS IPs when there is a wireless connection. Any work around to save me reloading these IPs at every logon?
__________________

---

