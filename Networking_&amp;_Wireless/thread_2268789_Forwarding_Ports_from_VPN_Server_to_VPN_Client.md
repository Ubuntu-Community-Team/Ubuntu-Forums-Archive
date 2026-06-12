---
title: "Forwarding Ports from VPN Server to VPN Client"
date: 2015-03-11
forum: Networking &amp; Wireless
---

### Post by M1GEO on 2015-03-11
Hello folks.

I wonder if anyone can advise me. I nearly have this going based on lots of other forum posts, but, I'm still a bit stuck.  I can forward ports for TCP but not for UDP. I am not sure why. The how-to I followed ([here]("http://unix.stackexchange.com/questions/55791/port-forward-to-vpn-client")) claims it works for both TCP and UDP, but it doesn't for me.

I wrote a small script that I want to run to forward the ports, which is based on the above link:

```
#!/bin/bash

WANIP="<public IP of VPN server>"
SRVIP="10.0.0.1"
CLIIP="10.0.0.2"

ForwardPort () {
        PORT=$1
        PROT=$2
        echo "Forwarding connections to $WANIP:$PORT/$PROT to $CLIIP:$PORT/$PROT via $SRVIP"
        iptables -t nat -A PREROUTING -d $WANIP -p $PROT --dport $PORT -j DNAT --to-dest $CLIIP:$PORT
        iptables -t nat -A POSTROUTING -d $CLIIP -p $PROT --dport $PORT -j SNAT --to-source $SRVIP
}

ForwardPort 40000 udp
ForwardPort 40001 tcp
for P in 20001 20002 20003 20004 20005 
do
        ForwardPort $P udp
        ForwardPort $P tcp
done
```

As you can see, I want ports 20001 20002 20003 20004 20005 forwarded both UDP and TCP, port 40000 UDP, 40001 TCP.

With this script, all of the TCP forwarding works, all of the UDP doesn't. I have all the internet routed from the client through the VPN, and everything else seems to work fine.

Any pointers greatly appreciated ;) Cheers!

---

### Post by M1GEO on 2015-03-11
Please ignore this question. It seems, after much struggling on my part, there was an issue with the remote server testing the connections.  This has been fixed and now confirms the ports are open and forwarded as expected.

Left here for completeness.

---

