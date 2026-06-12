---
title: "DNS update from DHCP generating errors (I think)"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by bturrie on 2008-03-02
I sort of thought I had this figured out, but apparently not.

I have dhcp3-server and bind9 installed on a Vmware xubuntu feisty machine (pdc1). I have a second virtual machine as a backup (slave) dns. Both seem to be working just fine with the master updating changes on the slave. The dhcp server seems to be working as well. Today I tried to get dhcp to update my dns. 

It sort of works but there's odd looking stuff in the syslog that has me thinking all is not well.

here it is

Mar  2 09:05:54 pdc1 named[4162]: client 127.0.0.1#1029: updating zone 'turriehome.com/IN': adding an RR at 'bachvm.turriehome.com' A
Mar  2 09:05:54 pdc1 named[4162]: client 127.0.0.1#1029: updating zone 'turriehome.com/IN': adding an RR at 'bachvm.turriehome.com' TXT
Mar  2 09:05:54 pdc1 named[4162]: /etc/bind/zones/turriehome.com.hosts.jnl: open: permission denied
Mar  2 09:05:54 pdc1 named[4162]: client 127.0.0.1#1029: updating zone 'turriehome.com/IN': error: journal open failed: unexpected error
Mar  2 09:05:54 pdc1 dhcpd: Unable to add forward map from bachvm.turriehome.com. to 192.168.1.14: timed out
Mar  2 09:05:54 pdc1 dhcpd: DHCPREQUEST for 192.168.1.14 from 00:0c:29:b4:d4:fa (bachvm) via eth0
Mar  2 09:05:54 pdc1 dhcpd: DHCPACK on 192.168.1.14 to 00:0c:29:b4:d4:fa (bachvm) via eth0
Mar  2 09:06:11 pdc1 named[4162]: client 127.0.0.1#1029: updating zone 'turriehome.com/IN': adding an RR at 'escher.turriehome.com' A
Mar  2 09:06:11 pdc1 named[4162]: client 127.0.0.1#1029: updating zone 'turriehome.com/IN': adding an RR at 'escher.turriehome.com' TXT
Mar  2 09:06:11 pdc1 named[4162]: /etc/bind/zones/turriehome.com.hosts.jnl: open: permission denied
Mar  2 09:06:11 pdc1 named[4162]: client 127.0.0.1#1029: updating zone 'turriehome.com/IN': error: journal open failed: unexpected error
Mar  2 09:06:11 pdc1 dhcpd: Unable to add forward map from escher.turriehome.com. to 192.168.1.12: timed out
Mar  2 09:06:11 pdc1 dhcpd: DHCPREQUEST for 192.168.1.12 from 00:1a:4d:9f:19:78 (escher) via eth0
Mar  2 09:06:11 pdc1 dhcpd: DHCPACK on 192.168.1.12 to 00:1a:4d:9f:19:78 (escher) via eth0

Here are the relevant parts of dhcp.conf

server-identifier     server;
ddns-updates on;
ddns-update-style     interim;
ddns-domainname     "turriehome.com.";
ddns-rev-domainname     "in-addr.arpa";
ignore     client-updates;
include		"/etc/bind/rndc.key";

zone turriehome.com. {
	primary 127.0.0.1;
	key rndc-key;
}

 and heres the stuff in named.conf.local

zone "turriehome.com" {
     type master;
     file "/etc/bind/zones/turriehome.com.hosts";
     allow-update { key "rndc-key"; };
     notify yes;
	allow-transfer {
		192.168.1.5;
	};
     };
zone "1.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/192.168.1.com.hosts";
     allow-update { key "rndc-key"; };
     notify yes;
     allow-transfer {
		192.168.1.5;
	};
     };

include "/etc/bind/rndc.key";

I'm not sure what journal file it's talking about but earlier I needed to create a file

/etc/bind/zones/turriehome.com.hosts.jnl

That got rid of one set of errors but then I got the above stuff from syslog. I'm sort of lost...

As it turns out, I needed to change the permissions on the /etc/bind/zones directory so that DHCP could write to my zones files.

here's a good reference I found while I was researching the issue

[http://doc.gwos.org/doku.php/doc:admin:dynamicdns](http://doc.gwos.org/doku.php/doc:admin:dynamicdns)

---

### Post by djdvant on 2008-04-24
After much hair pulling over several months I finally got to the problem.  My DNS and DHCP files were OK and always had been.

I finally tracked down an kernel audit message


kernel:  audit(1209076817.081:16): type=1503 operation="inode_create" requested_mask="w::" denied_mask="w::" name="/etc/bind/xxxxx.com.hosts.jnl" pid=16561 profile="/usr/sbin/named" namespace="default"

So I had a look in:
/etc/apparmor.d/usr.sbin.named

and changed this line:
  /etc/bind/** r,

to this:
  /etc/bind/** rw,

End of problems

---

### Post by styelz on 2008-06-21
It states in /etc/apparmor.d/usr.sbin.named ...

  # /var/lib/bind is for dynamically updated zone (and journal) files.

Moving these zones to this directory also fixes the issue, and is probably the correct way of doing it.

---

