---
title: "samba tries to use stale DHCP info?"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by jlrubin on 2008-07-24
I use Ubuntu as a file server for my home windows network. Samba is the WINS server. I changed NICs, renumbered IP addresses, etc, and now Samba is trying to talk to another master browser that no longer exists:

```
Jul 24 16:07:01 robin nmbd[5296]: [2008/07/24 16:07:01, 0] nmbd/nmbd_browsesync.c:get_domain_master_name_node_status_fail(486) 
Jul 24 16:07:01 robin nmbd[5296]:   get_domain_master_name_node_status_fail: 
Jul 24 16:07:01 robin nmbd[5296]:   Doing a node status request to the domain master browser at IP 192.168.1.5 failed. 
Jul 24 16:07:01 robin nmbd[5296]:   Cannot get workgroup name. 
```

Everything works, but I want to get this stuff out of my logs and I want to understand what is happening.
I think Samba is getting the IP address 192.168.1.5 from old DHCP leases I can see in /var/lib/dhcp3. How do I make this go away?

Here's lease info from eth0, which is no longer used.

```
lease {
  interface "eth0";
  fixed-address 192.168.1.5;
  option subnet-mask 255.255.255.0;
  option routers 192.168.1.1;
  option dhcp-lease-time 86400;
  option dhcp-message-type 5;
  option domain-name-servers 208.67.222.222,208.67.220.220;
  option dhcp-server-identifier 192.168.1.1;
  option dhcp-renewal-time 43200;
  option dhcp-rebinding-time 75600;
  option host-name "robin";
  option netbios-name-servers 192.168.1.5;
  option domain-name ".";
  renew 4 2008/6/26 22:42:10;
  rebind 4 2008/6/26 22:42:10;
  expire 4 2008/6/26 22:42:10;

```

---

