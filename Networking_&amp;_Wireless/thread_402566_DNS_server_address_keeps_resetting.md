---
title: "DNS server address keeps resetting"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by kargath64 on 2007-04-05
My computer specs are as follows.
ASUS A8N-VM-CSM mobo (NFORCE4 based, with inbuilt ethernet and sound)
AMD64 3800+ dual core CPU
160GB HDD
NVIDIA 6600GT graphics card
I also dual-boot with WinXP Home.
I use Dapper Drake, with the upgraded kernel from the standard repository.

My problem is simple - the DNS in the "Network Setting" > DNS tab keeps resetting itself to an invalid address and deleting the proper one, without any input/changes from me.  I want it to stay at 203.8.183.1 - any ideas?

---

### Post by spd106 on 2007-04-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/25624](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/25624) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Try adding the name server to the /etc/network/interfaces file as outlined in the bug report. 

Alternatively, you can add it to the dhclient.conf as outlined here [http://ubuntuforums.org/showthread.php?t=295567](http://ubuntuforums.org/showthread.php?t=295567)

---

### Post by ariel on 2007-04-15
I had a somewhat related problem.

You may get some hints from here:

[http://ubuntuforums.org/showthread.php?t=408866](http://ubuntuforums.org/showthread.php?t=408866)

---

### Post by archon256 on 2008-02-01
I realised that my router was resetting the DNS to the wrong 192.168.1.1 every 10 seconds and even if I wrote via Network Settings (KDE) or directly into resolv.conf to use an alternative good one (194.72.6.51) after 10 seconds it got overwritten again to the 192.168.1.1  I was getting desperate and furious. Windows machines kept the alternate DNS in IP configuration without problems. 
Then I found out (through a OpenSuse Live CD and YAST configuration) that to turn off the setting DNS via DHCP I had to change the resolv.conf instead of 

search -name-
nameserver 192.168.1.1

to 

domain site 
nameserver 192.168.1.1
nameserver 194.72.6.51

That helped, since then the DNS stays as it should and my internet is working 100%

---

### Post by netztier on 2008-02-01
> **archon256 said:**
> I realised that my router was resetting the DNS to the wrong 192.168.1.1 every 10 seconds and even if I wrote via Network Settings (KDE) or directly into resolv.conf to use an alternative good one (194.72.6.51) after 10 seconds it got overwritten again to the 192.168.1.1  I was getting desperate and furious. Windows machines kept the alternate DNS in IP configuration without problems. 
Then I found out (through a OpenSuse Live CD and YAST configuration) that to turn off the setting DNS via DHCP I had to change the resolv.conf instead of 

search -name-
nameserver 192.168.1.1

to 

domain site 
nameserver 192.168.1.1
nameserver 194.72.6.51

That helped, since then the DNS stays as it should and my internet is working 100%

Solution found, but by a rough approach.

It wasn't your router's fault, but your DHCP client's. When the DHCP client on your ubuntu box renews its address lease from the (probably router-built-in) DHCP server, the DHCP reply also contains the DNS server address. And, as every good DHCP client should do, it puts this information in /etc/resolv.conf.

If you wanted to make sure that there is always your preferred DNS in /etc/resolv.conf, you should edit **/etc/dhcp/dhcpclient.conf**, and uncomment & edit the red line to hold your preferred DNS.

```
send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
[COLOR="Red"]prepend domain-name-servers 194.72.6.51;[/COLOR]
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
```

Like this, there will always be 194.72.6.51 in your /etc/resolv.conf, regardless what any DHCP server might give as DNS server information. This however has a drawback: say - you're in someone else's network for some time, and 194.72.6.51 is not reachable for you, but the local DNS would be. Your PC now would always try to contact your preferred-DNS first - and would have to let the lookup timeout interval pass before asking the second DNS. Not good - gives an awful web browsing experience.

So the best alternative would be to talk your existing router into telling the clients to use 194.72.6.51 as DNS instead of 192.168.1.1 - provided the configuration options allow for this.

I assume that you encounter these problems because the DNS proxy in your router is of the ones that are "broken" in that they don't work with Linux (but do with Windows). Maybe a firmware upgrade on the router will fix the issue, so that you can allow it's built-in DHCP server to announce 192.168.1.1 as DNS to the DHCP clients - while the router itself learns to use 194.72.6.51 from the ISP, by either being a DHCP client (facing towards the internet) or a PPPoE client to your ISP. Then, the DNS proxy will act as DNS server to the inside and as DNS client towards the ISP.

regards

Marc

---

### Post by kevdog on 2008-02-01
Or you could just try appending OpenDNS servers to your prepend list which should be available from any computer.  Im not always an OpenDNS fan, however the solution should be universal.

---

