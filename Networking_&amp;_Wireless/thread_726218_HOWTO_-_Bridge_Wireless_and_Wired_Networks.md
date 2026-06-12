---
title: "HOWTO - Bridge Wireless and Wired Networks"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by sasa_2000_2003 on 2008-03-16
Hi  :) ,

This is my first time to ask , i usually find everything in here, but this time i am completely lost ......

Before i ask , I am a beginner not a pro ....

now i have 2 laptops , Laptop "A" and Laptop "B"....
and i have a network cable connected to "A" which allow me to access the DSL , i need to create a wireless network ( for example named : mynetwork ) , and bridge eth0 with eth1 together and allow Laptop "B" to :
1) connect on Laptop "A" wireless network "mynetwork" ....
2) Use the DSL ....

how can i create a wireless network ? and how can i bridge the two interfaces ????

I am using ubuntu 7.10 ,,,,,

Thanks in advance .....

---

### Post by Xbehave on 2008-04-17
I think its covered here : 
[https://help.ubuntu.com/community/BridgingNetworkInterfaces?](https://help.ubuntu.com/community/BridgingNetworkInterfaces?)
& [https://help.ubuntu.com/community/NetworkConnectionBridge?](https://help.ubuntu.com/community/NetworkConnectionBridge?)
It can also be done with firewall configuration tool like guarddog or firestarer

and while your at it you may want to vote for [this](http://brainstorm.ubuntu.com/idea/825/)
[[IMG]http://brainstorm.ubuntu.com/idea/825/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/825/)

---

### Post by Paris Heng on 2008-04-17
> **sasa_2000_2003 said:**
> Hi  :) ,

This is my first time to ask , i usually find everything in here, but this time i am completely lost ......

Before i ask , I am a beginner not a pro ....

now i have 2 laptops , Laptop "A" and Laptop "B"....
and i have a network cable connected to "A" which allow me to access the DSL , i need to create a wireless network ( for example named : mynetwork ) , and bridge eth0 with eth1 together and allow Laptop "B" to :
1) connect on Laptop "A" wireless network "mynetwork" ....
2) Use the DSL ....

how can i create a wireless network ? and how can i bridge the two interfaces ????

I am using ubuntu 7.10 ,,,,,

Thanks in advance .....

Hi, no need to bridge!!! Bridge is old fashion to do. Just simply add the routing in the Kernel routing table + set the iptables + ipv4 forward. Follows the below:

1. Add route in the routing table for the 2 particular interfaces using route add ... roughly like this, depend on your network configuration.


> route add -net [COLOR="Red"]<IP>[/COLOR] netmask [COLOR="Red"]<mask>[/COLOR] dev [COLOR="Red"]<interface>[/COLOR]
route add default gw [COLOR="Red"]<IP>[/COLOR] dev [COLOR="Red"]<interface>[/COLOR]

2. Check the routing table, route -n

3. Enable ip forwarding, i think the case mayb ipv4.

> echo 1 > /proc/sys/net/ipv4/ip_forward

4. Using NAT in the PC for private to public address translation, i think your out-going interface will be eth0.

> modprobe iptable_nat
iptables -F
iptables -t nat -F
iptables -t nat -A POSTROUTING -o [COLOR="Red"]<out-going interface>[/COLOR] -j MASQUERADE
iptables-save > /etc/iptables.conf

---

