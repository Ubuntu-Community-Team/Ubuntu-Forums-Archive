---
title: "DHCP integration with Hosts"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by LMSSML on 2007-11-07
Hi people,


I would like to know if this is correct.

We could define on hosts something like this

host aaaaa{
hardware ethernet < MAC address>
host address <IP address>
}

Then we could add to the DHCP the following line

include /etc/hosts

But it always get an error on the last line is it missing something.

Thanks.

---

### Post by spd106 on 2007-11-07
Check you've added a semi-colon to the end of every statement.

I'm assuming that you are editing the /etc/dhcp3/dhcpd.conf file.

---

### Post by LMSSML on 2007-11-07
This I'm using in hosts

> host aaaaa{
hardware ethernet < MAC address>
host address <IP address>
}

and when I do a nono /etc/dhcp3/dhcpd.conf file. I use that command an include that the dhcpd goes to my hosts and see what restrictions it has.

---

### Post by LMSSML on 2007-11-07
Does anyone knows what is missing

---

