---
title: "Ubuntu repo servers always going to 1.0.0.0"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by masked_marsoe on 2007-04-07
When ever I try to get a new package, using apt-get or the update manager or whatever, it will search 1.0.0.0.

It doesn't matter if it's the local (NZ) server, or the main ubuntu ones. 

My DNS due to the router (D Link 504T) always resets itself to 10.0.0.0 (giving me no internet access), so I have to manually enter in my ISP's DNS. 

And occasionally, the apt-get (.etc) will work. But 90% of the time it doesn't.

If there's some way to lock in the manual DNS, I think that'll fix it. 

Any ideas?

---

### Post by dbott67 on 2007-04-07
You can try manually adding the OpenDNS servers to your /etc/resolv.conf file and comment out your current one:
```
sudo gedit /etc/resolv.conf
``````
[B][COLOR=Red]nameserver 208.67.222.222
nameserver 208.67.220.220[/COLOR][/B]
**[COLOR=Red]#[/COLOR]** nameserver 192.168.1.1
```If you notice an improvement (or it cures the problem) then you can make it permanent. By default, the dhclient.conf file will overwrite the resolv.conf file each reboot, so you need to edit the file:

1. Backup the file first:
```
sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.conf.bak
```2. Edit the dhclient.conf file:
```
sudo gedit /etc/dhcp3/dhclient.conf
```3. Look for the following line:
```
#prepend domain-name-servers 127.0.0.1;
```Remove the comment (#) and change it to:
```
prepend domain-name-servers **[COLOR=Red]208.67.222.222, 208.67.220.220[/COLOR]**;
```4. Next, look for the **[COLOR=Red]domain-name-servers,[/COLOR]** and ***remove*** it:

```
**[COLOR=Blue]prepend domain-name-servers 208.67.222.222, 208.67.220.220;[/COLOR]**
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, **[COLOR=Red]domain-name-servers,[/COLOR]** host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
```5. Restart your network
```
dbott@edgy:~$ sudo/etc/init.d/networking restart
```
-Dave

---

### Post by masked_marsoe on 2007-04-07
Heh, the answer was quite easy, and if you have the same problem, you can find the right instructions at [http://doc.gwos.org/index.php/Router_DNS_Problems](http://doc.gwos.org/index.php/Router_DNS_Problems)

With the DNS locked at the correct servers, the DNS will no longer revert to 10.0.0.0, and will not search for things at 1.0.0.0

---

### Post by dbott67 on 2007-04-07
Glad you got it working.

The downside to using my method is that it prevents any local DNS server from being used (although, you could always leave step #4 in place; the DNS search order would be OpenDNS first, followed by the local one).  The upside is that if the computer is portable, it can be moved from network to network without issues and the necessary files will be updated as required.

If you "lock" the resolv.conf file (using chattr +i) you may have issues if you use a different network, as you will prevent your DNS servers from being updated.

In either case, be sure to document what changes you make so that you can undo them if need arises.

-Dave

---

