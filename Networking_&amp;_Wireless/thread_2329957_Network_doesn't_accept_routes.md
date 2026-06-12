---
title: "Network doesn't accept routes"
date: 2016-07-06
forum: Networking &amp; Wireless
---

### Post by ulrich-prinz on 2016-07-06
Hi!

I do run a 15.10 based server (that has been upgraded from 14.x to 15.04 and then to 15.10). I need to add two static routes to it and that is only possible by manually setting them on the console. I found no other way to do that automatically after boot.

The basic configuration is dynamic, so a DHCP server is providing all network data to all machines including this server.

/etc/network/interfaces 
... is mostly untouched for dhcp at eth0. I tried adding "up route add -net ..." in that file and the routes seem to be up for a short while as connections. Trying to connect over one of the routes gets a connection refused as long as SSH is not started. But before ssh comes up, the connections ceases. No response or "Connection time out".

I removed the routes from /etc/network/interfaces and installed the packet ifupdown-extra and added both routes to the /etc/network/routes file. This ends in the same result, while the kernel boots, the routes are available, but when all the services start, someone seems to clean out all routes and if fails over from "Connection refused" to "Connection timed out".

Another trial was to set the routes at the DHCP server. It results in the same behavior and I am actually out of ideas now.
I read a lot across the net and I am confused by if and how to enable or set NetworkManager-wait-online.service and its friends. However I didn't expect that adding two simple routes could be so complicated.

In syslog I can see some info:
```
Jul  6 16:28:48 jk-compile connmand[935]: The name net.connman.vpn was not provided by any .service files
Jul  6 16:28:48 jk-compile connmand[935]: lo {newlink} index 1 operstate 0 <UNKNOWN>
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {create} index 2 type 1 <ETHER>
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {RX} 42 packets 5577 bytes
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {TX} 28 packets 2736 bytes
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {update} flags 36866 <DOWN>
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {newlink} index 2 address 00:aa:bb:cc:dd:00 mtu 1500
Jul  6 16:28:48 jk-compile systemd[1]: NetworkManager-wait-online.service: Cannot add dependency job, ignoring: Unit NetworkManager-wait-online.service is masked.
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {newlink} index 2 operstate 2 <DOWN>
Jul  6 16:28:48 jk-compile connmand[935]: Adding interface eth0 [ ethernet ]
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {RX} 42 packets 5577 bytes
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {TX} 28 packets 2736 bytes
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {update} flags 102467 <UP,RUNNING,LOWER_UP>
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {newlink} index 2 address 00:aa:bb:cc:dd:00 mtu 1500
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {newlink} index 2 operstate 6 <UP>
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {add} route fe80:: gw :: scope 0 <UNIVERSE>
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {RX} 42 packets 5577 bytes
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {TX} 28 packets 2736 bytes
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {newlink} index 2 address 00:aa:bb:cc:dd:00 mtu 1500
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {newlink} index 2 operstate 6 <UP>
Jul  6 16:28:48 jk-compile systemd[1]: NetworkManager-wait-online.service: Cannot add dependency job, ignoring: Unit NetworkManager-wait-online.service is masked.
...
Jul  6 16:28:48 jk-compile systemd[1]: Started Modem Manager.
Jul  6 16:28:48 jk-compile connmand[935]: Skipping disconnect of carrier, network is connecting.
Jul  6 16:28:48 jk-compile connmand[935]: Setting domainname to eurooel.local
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {add} address 192.168.200.228/24 label eth0 family 2
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {add} route 192.168.200.0 gw 0.0.0.0 scope 253 <LINK>
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {add} route 192.168.200.249 gw 0.0.0.0 scope 253 <LINK>
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {add} route 0.0.0.0 gw 192.168.200.249 scope 0 <UNIVERSE>
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {add} route 82.165.8.211 gw 192.168.200.249 scope 0 <UNIVERSE>
Jul  6 16:28:48 jk-compile whoopsie[964]: [16:28:48] offline
Jul  6 16:28:48 jk-compile connmand[935]: eth0 {del} route 82.165.8.211 gw 192.168.200.249 scope 0 <UNIVERSE>

```

A sidenote may be that I did not configure anything to reach out for 82.165.8.211... But I guess it is the connman trying to find out about the internet availability on that interface.

So any idea, of how to set NetworkManager and /etc/network/interfaces to simply add my two routes automatically? Cause manually it works fine...

Cheers!
Astralix

---

### Post by TheFu on 2016-07-06
Welcome to the forums.

Don't use network manager and this stuff works like you expect. Best to purge those packages whenever non-standard networking is needed. Many GUI tools only work well for the most common situation. If something different is needed, best to drop them and handle it the old-school way.

IMHO.

BTW, 15.10 support ends this month. Time to move to a supported release. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

If you want specific help, please post specific files, routes and data.

---

### Post by ulrich-prinz on 2016-07-07
Hi TheFu!

Thank you for your reply.

We removed Intel connman and also removed the ifupdown-extra package, which introduced some extra errors in the syslog. But these are already known and documented in the projects bug trackers.
Removing all this lead to a state where we got the static routes supplied by DHCP option 121. But this time we lost option 3, the default route.

However, we took the downtime to upgrade to 16.04 as you stated and everything is up and running...

...except the issue that option 03 for the default route is still ignored as soon as we added option 121 static routes.
The corresponding RFC3442 advises to add the default route to both options 03 and 121 to provide mechanisms for clients the support only one of the options. The probably most idiotic thing now is, that linux seem to ignore 03 when 121 is present, but the DHCP server (MS Sverer 2008R2) does not allow to set 0.0.0.0 in its static routes...

[Edit] A false entry in the static routing table option 121 somehow voided the default route. Now it is working!

So solution was:
remove ifupdown-extras
remove connman
fill extra and defaults routes correctly in option 121 of the DHCP server
reboot and you're in!

Thanks
Astralix

---

### Post by TheFu on 2016-07-07
Please mark as "**solved**" if this is working. I can't tell from the last reply.  

We don't use Windows for infrastructure here, so I wouldn't know **anything** about "option" 03/121 - you lost me referencing that stuff.

BTW, there are hundreds of ways to add routes to any Unix system, but the best way (IMHO) is to use the /etc/network/interfaces solution. This way routes are added and removed as an interface is brought up and down. The other methods would usually only work at boot time - assuming NM and other end-user tools like that aren't used.

---

### Post by ulrich-prinz on 2016-07-08
[COLOR=#000000]TheFu,

Options 03 and 121 are pure plain DHCP option fields. These are send out to (and sometimes received by) the DHCP server to a requesting DHCP client.
These options are basic networking and defined in these request for comments by the IETF. For the unclassified routing table option 121 the appropriate RFC is
[/COLOR]https://tools.ietf.org/html/rfc3442
These have nothing to do with Windows, except that a Windows DHCP server must supply them exactly as a Linux system should do it.

As you might have read, we tried entering the routes to /etc/network/interfaces and exactly that did not work. So we went over to the DHCP system as we tried to come around that problem that the local configuration did not work.

A nice side-effect is now, that a planned network upgrade requires only changes on one machine (the DHCP server) and the connected machines will get updated to the new configuration automatically. No need for editing dozens of /etc/network/interfaces files :)

Cya
Astralix

---

### Post by TheFu on 2016-07-08
Glad you found a workable solution.

If I need to modify a file on multiple systems, there are many tools for that.
* tiny script to copy the file
* DevOps tool - ansible, puppet, chef, cfengine, salt, rexify, and 20K home-built solutions.
Both of these are very, very, very commonly used. They leverage ssh.

If you do want to find out why changes to the interfaces file didn't work, please post it, the complete file. Sometimes there are bugs, but usually not.

---

