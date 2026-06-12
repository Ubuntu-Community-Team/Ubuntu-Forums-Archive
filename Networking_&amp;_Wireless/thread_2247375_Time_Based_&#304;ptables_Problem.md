---
title: "Time Based &#304;ptables Problem"
date: 2014-10-07
forum: Networking &amp; Wireless
---

### Post by secoonder on 2014-10-07
Hello
 I am using iptables rules in a linux gateway (ubuntu server 12.04) and  all works good. I configured a transparent squid proxy and works too.

i would like to allow incoming rdp access only available  between 8 AM to 19:00 PM
i added this rule:
iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 3389 -j DNAT --to 192.168.1.44 -m time --timestart 08:00 --timestop 19:00 --weekdays Sun,Mon,Tue,wed,Thu,Fri,Sat
When i added rule,i did not take error.
But,this rule **was not** run succesfully.**it is still rdp accessed before 8 AM and after 19:00 PM  ? **i cant solve this situation.
Can you help me ?
Thank you very much
Kind Regards

---

### Post by SeijiSensei on 2014-10-07
I don't know if this is the reason, but "Wed" is not capitalized like the other days.

---

### Post by secoonder on 2014-10-08
i wrote wrong here.My Rule:
iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 3389 -j DNAT --to  192.168.1.44 -m time --timestart 08:00 --timestop 19:00 --weekdays  Sun,Mon,Tue,**W**ed,Thu,Fri,Sat
**it is still rdp accessed before 8 AM and after 19:00 PM  ? **i cant solve this situation.
Can you help me ?
Thank you very much
Kind Regards

---

### Post by Doug S on 2014-10-08
Very interesting. I did not know about this iptables time module, so I tried it. On my system it is working as expected. I can get port forwarding to work or not work based on the (UTC) time I set. Example:```
$IPTABLES -t nat -A PREROUTING -p tcp -i $EXTIF --dport 8083 -j DNAT --to 192.168.111.112:80 -m time --timestart 17:00 --timestop 23:00 --weekdays Sun,Mon,Tue,Wed
```gives:```
doug@doug-64:~/init$ [COLOR=#ff0000]sudo iptables -t nat -v -x -n -L | more[/COLOR]
Chain PREROUTING (policy ACCEPT 5 packets, 232 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       [COLOR=#ff0000]1 [/COLOR]      60 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8083 [COLOR=#ff0000]TIME from 17:00:00 to 23:00:00[/COLOR] on Mon,Tue,Wed,Sun UTC to:192.168.111.112:80
```And if I change the time range so that it is not valid right now, that path is not traversed in the PREROUTING table. Example (I still had every day of the week enabled for this one)```
doug@doug-64:~/init$ [COLOR=#ff0000]sudo iptables -t nat -v -x -n -L | more[/COLOR]
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination
       [COLOR=#ff0000]0 [/COLOR]       0 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8083 [COLOR=#ff0000]TIME from 08:00:00 to 19:00:00[/COLOR] UTC to:192.168.111.112:80
```It was just after 19:00 UTC when I did these experiments.

---

### Post by secoonder on 2014-10-18
The Problem is solved :D
i want to allowed between 08:00 AM  and 19:00 PM.i wrote:
iptables -t nat -A PREROUTING -p tcp -i eth0 --dport 3389 -j DNAT --to  192.168.1.44 -m time --timestart **05:00 **--timestop **16:00** --weekdays  Sun,Mon,Tue,wed,Thu,Fri,Sat
above ,When i get back 3 hours,this rule run.Very interesting :D
Thank you very much for your help
Regards

---

