---
title: "restrict an ip address using linux firewall"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by tocleora on 2008-03-26
I need to restrict an ip range (say, 10.10.30.0/24) from being able to access anything but a few web sites, e-mail and instant messenger using linux firewall.  At one time I had at least the web part locked down but a colleague told me I didn't do it right. I had done it in prerouting and he said that wasn't the right place (even though it worked).  So where SHOULD I do it and how would I structure that?  Thanks for any assistance.

---

### Post by SpaceTeddy on 2008-03-27
anything in the nat and mangle table should always stay on accept, as these rules do not filter (as the name of the chain says) but nat and mangle (doh :) )

any dropping allowing is always done in the standard table - in your case most likely the FORWARD Chain...

so, lets say you only want to allow outgoing port 80 - nothing else - just port 80 to anyone... 

this rule will drop ANYTHING that runs through your computer. it will completly shut down any traffic passing thought you it.
> sudo iptables -P FORWARD DROP

next, we define a rule that will allow existing connections to pass, but reject new ones.
> sudo iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT 
this rule alone does not make any sense at all, since there is still nothing that can pass, but with it in the ruleset, you now only have to specifiy from where to where new connections can be initatied - and this rule will then worry about the rest..

from here, you now specifially allow fromwhere to where people can connect to which port using what protocoll. lets say you now what to allow outgoing connections to any website... you would use...
> sudo iptables -A FORWARD -m state --state NEW -p tcp --dport 80 -j ACCEPT

let's look at that a litte closer... 
> -m state --state
this says that this rule only applies to NEW connections. How this works in detail does not matter - it just works :)
> -p tcp --dport 80
these are the specifics of the connetions. it needs to be the tcp protocoll and it needs to be directed towards a port 80 (webserver)... you can define pretty much anything here. but you probably know this already

lastly, the
> -j ACCEPT

overwrites the default policy (which is the first thing we did - drop anything) and lets pakets that match this rule pass. Again, once this paket it passed, the first rule will worry about it. this one only accepts the first paket.

hope this helps :)

---

### Post by tocleora on 2008-03-27
that helped, thanks

---

