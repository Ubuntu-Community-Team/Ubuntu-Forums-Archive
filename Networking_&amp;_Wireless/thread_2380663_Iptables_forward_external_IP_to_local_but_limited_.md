---
title: "Iptables forward external IP to local but limited for custom IPs only."
date: 2017-12-20
forum: Networking &amp; Wireless
---

### Post by horizn on 2017-12-20
Hi,
I don't know if it possible to this in that way, but I'd like to forward external IP address to the local one (with NAT), but limit its availability for custom IP or list of IPs. So what I have done so far with success is:
```

iptables -A FORWARD -s 0/0 -d 192.168.x.y -j ACCEPT
iptables -A FORWARD -s 192.168.x.y -d 0/0 -j ACCEPT

iptables -t nat -A PREROUTING -s 0/0 -d 1.2.3.4 -j DNAT --to 192.168.x.y
iptables -t nat -A POSTROUTING -s 192.168.x.y -d 0/0 -j SNAT --to 1.2.3.4

```

So the easiest way should be replacing 0/0 with IP or list of IPs, however in my configuration I have:

```

for i in `cat ${0%$START_FILE}rc.fire_ip_nat | cut -d'#' -f1`
      do
        EXT_IP=`echo $i | cut -d';' -f1`
        LOCAL_IP=`echo $i | cut -d';' -f2`

        iptables -A FORWARD -s 0/0 -d $LOCAL_IP -j ACCEPT
        iptables -A FORWARD -s $LOCAL_IP -d 0/0 -j ACCEPT

        iptables -t nat -A PREROUTING -s 0/0 -d $EXT_IP -j DNAT --to $LOCAL_IP
        iptables -t nat -A POSTROUTING -s $LOCAL_IP -d 0/0 -j SNAT --to $EXT_IP

```

where $LOCAL_IP and $EXT_IP are defined in another configuration file to avoid repeating above rule hundreds of time, and the line for each IP looks like: 1.2.3.4;192.168.x.y
Ideally will be to add something like

```

for i in `cat ${0%$START_FILE}rc.fire_ip_nat | cut -d'#' -f1`
      do
        EXT_IP=`echo $i | cut -d';' -f1`
        LOCAL_IP=`echo $i | cut -d';' -f2`
        SECURE=`echo $i | cut -d';' -f3`

        if [ ! "$SECURE" == "all" ]; then
            SECURITY="-s $SECURE"
        else
            SECURITY=""
        fi

        iptables -A FORWARD -s 0/0 -d $LOCAL_IP -j ACCEPT
        iptables -A FORWARD -s $LOCAL_IP -d 0/0 -j ACCEPT

        iptables -t nat -A PREROUTING -s 0/0 -d $EXT_IP -j DNAT --to $LOCAL_IP
        iptables -t nat -A POSTROUTING -s $LOCAL_IP -d 0/0 -j SNAT --to $EXT_IP

```

and then modify each line in the configuration file by adding ;all or define IPs there to looks like: 1.2.3.4;192.168.x.y;5.5.5.5/32,6.6.6.6/32,12.12.12.0/24. But how to do it for both source "-s" and destination "-d"?

---

