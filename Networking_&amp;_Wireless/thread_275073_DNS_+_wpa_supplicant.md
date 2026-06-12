---
title: "DNS + wpa_supplicant"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by samm on 2006-10-10
I can successfully connect to my wifi router using wpa_supplicant on my Thinkpad T42.  However, it appears dns is failing shortly after establishing the connection to my router.  I noticed I can fix this by killing dhclient, then starting it again.  The problem returns a short while later, under 5 minutes.  Any idea why this happens?

Here is my resolve.conf and dhclient.ath0.leases contents:

```

samm@joule:~$ cat /var/lib/dhcp3/dhclient.ath0.leases
lease {
  interface "ath0";
  fixed-address 192.168.0.100;
  option subnet-mask 255.255.255.0;
  option routers 192.168.0.1;
  option dhcp-lease-time 604800;
  option dhcp-message-type 5;
  option dhcp-server-identifier 192.168.0.1;
  option domain-name-servers 192.168.0.1;
  option domain-name "roc.mn.charter.com";
  renew 3 2006/10/11 00:05:41;
  rebind 3 2006/10/11 00:05:41;
  expire 3 2006/10/11 00:05:41;
}
lease {
  interface "ath0";
  fixed-address 192.168.0.100;
  option subnet-mask 255.255.255.0;
  option routers 192.168.0.1;
  option dhcp-lease-time 604800;
  option dhcp-message-type 5;
  option dhcp-server-identifier 192.168.0.1;
  option domain-name-servers 192.168.0.1;
  option domain-name "roc.mn.charter.com";
  renew 6 2006/10/14 10:13:29;
  rebind 2 2006/10/17 03:06:07;
  expire 3 2006/10/18 00:06:07;
}
samm@joule:~$ cat /etc/resolv.conf
search roc.mn.charter.com
nameserver 192.168.1.1
samm@joule:~$

```

---

### Post by wieman01 on 2006-10-10
Is it only the DNS that is failing you or are you totally disconnected from the router? Can you still "ping" the router after the DNS has failed?

The difference is important because I may know a solution if you talk about a the entire network, not only the DNS.

If we are talking about the DNS only, then what you can try is to add this line in your under the corresponding "ath0" section in "/etc/network/interfaces".
> dns-nameservers [COLOR="Red"]xxx.xxx.xxx.xxx[/COLOR]
[COLOR="Red"]xxx.xxx.xxx.xxx[/COLOR] stands for any DNS, possibly the one that your ISP is providing. Then restart the network and see if it sticks:
> sudo /etc/init.d/networking restart

---

### Post by samm on 2006-10-11
Hi wieman, I am still able to ping my router after DNS has failed.  I'll try your solution tonight when I am at home and report back.

---

### Post by wieman01 on 2006-10-11
If that does not work, try to edit this file:
>  sudo gedit /etc/resolvconf/resolv.conf.d/base
Then add this line:
> nameserver [COLOR="Red"]192.168.xxx.xxx[/COLOR]
[COLOR="Red"]192.168.xxx.xxx[/COLOR] stands for you preferred DNS, be it the router or an external DNS provider. Then save the file & restart the computer.

---

