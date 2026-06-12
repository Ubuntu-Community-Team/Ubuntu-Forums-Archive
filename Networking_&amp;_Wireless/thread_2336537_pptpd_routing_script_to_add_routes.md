---
title: "pptpd routing script to add routes"
date: 2016-09-09
forum: Networking &amp; Wireless
---

### Post by chris9958 on 2016-09-09
Hi All


I have Ubuntu 14.04 on Amazon ec2 and have installed pptpd, this is connected into from a few Draytek routers (lan to lan) in various locations.  I use this to update the routing table on the Ubuntu server:-

```
#!/bin/bash


#This is /etc/ppp/ip-up.d/route-traffic


#router stretford
if [ "$6" == "11.22.33.44" ]; then
  route add -net 192.168.3.0 netmask 255.255.255.0 dev $1
fi


#router waddinton
if [ "$6" == "55.66.77.88" ]; then
  route add -net 192.168.196.0 netmask 255.255.255.0 dev $1
fi

```


This work great except that the IP addresses on the Dratek's are dynamic and sometimes change.

Is there an environment variable I can use to check to identify the username logging in?  I could us this to identify the router instead of the IP address and this would let me get around the dynamic IP address problem.

Thank you.

---

### Post by chris9958 on 2016-09-09
I managed to get it working like this:-

```
#!/bin/bash


VPNLOGINUSER="$(last $1 | grep 'still logged in' | grep -o '^[^ ]*')"


#chris
if [ "$VPNLOGINUSER" == "chris" ]; then
  route add -net 192.168.3.0 netmask 255.255.255.0 dev $1
fi


#roy
if [ "$VPNLOGINUSER" == "roy" ]; then
  route add -net 192.168.196.0 netmask 255.255.255.0 dev $1
fi
```

I would be happy to get any improvements on this.

Thanks.

---

