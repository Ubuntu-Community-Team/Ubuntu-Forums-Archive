---
title: "Setting up a secondary DNS Server (BIND9)"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by airspill on 2007-09-24
Hi,

I would like to setup BIND9 to act as a secondary DNS server to my primary (Windows Server 2003).

From what i heard, its pretty simple to do but i just cant find any clear directives how to do it. :(

How do i :

*A) Setup the primary (Win 2003) so it allows the replication on the secondary (Ubuntu BIND)?*

*B) Setup the secondary (Ubuntu) so it can connect to the primary to replicate the DNS entries?*

Any example config file would be appreciated.

Primary : 192.168.2.10
Secondary : 192.168.2.12

Thank you!

Jonathan

Edit: I forgot to mention : I don't need Active Directory support. thx.

---

### Post by helgman on 2007-09-25
Since I've never done this before I'll document every step so that you can follow what I've done. If things don't work out for me maybe we can figure out where it went wrong ...

First of my Windows DNS is based on Server 2003 Enterprise Edition SP2 and the Ubuntu server is 7.04 that runs on a VMware Server based on the Windows Server.

Windows Server: 192.168.2.10 (primary)
Ubuntu Server: 192.168.2.12 (secondary)

1. [Start on Ubuntu Server:] Set static IP-address of the Ubuntu Server.

2. Install bind ```
apt-get install bind
```
3. Edit **/etc/bind/named.conf.local**
```
zone "example.com" {
	type slave;
	file "/var/bind/example.com";
	masters { 192.168.2.10; };
	};
```
4. Create the directory for bind to store the file and create the file:
```
mkdir /var/bind
touch /var/bind/example.com
```
5. Make sure that the new configuration works by reloading the BIND-server:
```
/etc/init.d/bind reload
```
6. [Move to Windows Server] Create the Forward Lookup Zone in the Windows DNS snap-in (dnsmgmt). Guess this step can be omitted if you already have a zone.

7. Right-click and go for "Properites".

8. As default the server is set to do zone transfers to all servers listen in the "Name Server tab". This can be viewed and changed in the "Zone Transfer" tab.

9. Navigate to the "Name Server"-tab and "Add ...". Put the IP-address of the secondary DNS-server where the IP goes and press "Add". I put 192.168.2.12 in there for this example and I also added the FQDN of the server (*secondary.example.lan.*). Then press OK.

10. Create a few examples in the example.lan zone. Right-click in the right window and pick "New Host (A) ..." Just write the name of the machine (test1 or test2 or whatever name it should have) and type in the correct IP-address (192.168.2.120 for test1 and 192.168.2.130 for test2 in this example). I don't make any PTR since I don't have a reverse lookup zone at the moment.

11. [Back in Ubuntu] Let's grab that new zone file:
```
named-xfer -z example.lan -f /var/bind/example.lan 192.168.2.12
```

Now it should be up and running ... it is for me. I tried adding new hosts (on the Windows Server) and it worked like a charm. You might want to taka a look at security, but there is a lot of documentation and ideas about online so that should not be a problem.

Regards,
Helgman

---

