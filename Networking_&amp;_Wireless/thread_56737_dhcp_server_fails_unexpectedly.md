---
title: "dhcp server fails unexpectedly"
date: 2005-08-13
forum: Networking &amp; Wireless
---

### Post by logan2004 on 2005-08-13
hi,
After a  fair amount of time, my dhcp server fails unexpectedly. I am not sure exactly how long it will stop after, or if it is any certain amount of time, but I know that it has usually been sometime between 5 hours and 3 days. The following is the contents of my dhcpd.conf file:

```

#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

ddns-updates on;
ddns-update-style ad-hoc;
#option definitions common to all supported networks...
#option domain-name "example.org";
#option domain-name-servers ns1.example.org, ns2.example.org;

#default-lease-time 600;
#max-lease-time 7200;

authoritative;

subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.100 192.168.2.150;
  option domain-name-servers 68.168.96.5, 68.168.96.2;
  option domain-name "homenet.local";
  option routers 192.168.2.1;
  option broadcast-address 192.168.2.255;
  default-lease-time 600;
  max-lease-time 7200;
}

host router{
  hardware ethernet 00:13:10:89:f0:0d;
  fixed-address 192.168.2.1;
}

host livingroom{
  hardware ethernet 00:10:dc:e2:ae:30;
  fixed-address 192.168.2.50;
}
host shawna-laptop{
  hardware ethernet 00:0f:1f:ba:65:7a;
  fixed-address 192.168.2.51;
}

```

Any help would greatly be appreciated.

---

### Post by nad on 2005-08-14
Have you checked your log files for mail, messages and/or errors?

---

### Post by logan2004 on 2005-08-14
[QUOTE=nad]Have you checked your log files for mail, messages and/or errors?[/QUOTE]
 Im sorry, I'm not sure of how to check these. Could you please let me know?

Thanks

---

### Post by nad on 2005-08-14
Many log files are kept in /var/log .

The command: tail /var/log/messages  will show you the last 10 lines of the messages log.

The command: less /var/log/daemon.log will show you the current daemon log file one page at a time. With less you can scroll up or down with the arrow keys or page up and down with the page keys.

Peruse the other log files here also. You will learn much about your system. These are all text files, including your mail messages in /var/mail/user_name.

---

