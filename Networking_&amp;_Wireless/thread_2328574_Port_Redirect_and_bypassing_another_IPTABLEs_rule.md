---
title: "Port Redirect and bypassing another IPTABLEs rule"
date: 2016-06-22
forum: Networking &amp; Wireless
---

### Post by brian131 on 2016-06-22
First, this is really an IPtables question, but I feel like explaining why I'm trying to do what I'm doing, so forgive all the VOIP digression.

I have installed Asterisk on a server and added iptables rules to allow my VOIP providers to communicate with my server. I did this to keep the constant hacking attempts blocked, as my bandwidth is not that wide.  Port 5060 is like road kill to Buzzards in Georgia.

Anyway, I would also like to access the VOIP server using a softphone from a remote location.  Naturally, the fact I've only opened 5060 to my providers the access is blocked.  I added a rule redirecting another port (for the sake of argument we'll call it port 15060) to 5060, hoping I could then use a non-standard port and minimize the hack attempts. Asterisk doesn't, to the best of my knowledge, listen on more than one port.  

The problem is, the fact I'm filtering 5060 causes the connection to fail (or so it appears).

So, what I'd like to know, is there a way to set up iptables to only allow connections to port 5060 from the VOIP providers (as I've already done), but bypass this filter if there's a connection attempt from 15060 redirected to 5060 by iptables?

I hope the question makes sense and someone can provide some insight into how to do this (if it's even possible).

Thanks,

Brian

---

### Post by SeijiSensei on 2016-06-22
Sure. If you open 15060 with an INPUT rule, then forward it to the server's port 5060, you should get the results you seek.

```

/sbin/iptables -A INPUT -p tcp --dport 15060 -j ACCEPT
/sbin/iptables -t nat -A PREROUTING -p tcp -m tcp --dport 15060 -j DNAT --to-destination ip.of.ast.server:5060

```

You can also forward traffic with application-level proxies like [tcproxy]("https://github.com/dccmx/tcproxy"), or with xinetd's "redirect" directive.  The latter gives you more fine-grained control over repeated connection attempts and the like.

You also might write a more narrow INPUT rule.  For instance, if you know your mobile device will have a particular subnet address, I'd add an "-s 10.10.10.0/24" restriction to the INPUT rule above replacing 10.10.10.0/24 with the appropriate subnet address for your device.

---

### Post by brian131 on 2016-06-23
Thanks for the reply.

That's pretty close to what I tried (and I did try this as well). Both TCP and UDP. Same thing, registration times out. I can connect using 5060 on the lan because I have a rule allowing it, but redirected port doesn't fly :(.

I'll look at the tables and make sure I don't have something else in there that is getting in the way, but I don't think so.

Thanks again.

---

### Post by SeijiSensei on 2016-06-23
You might also need to enable packet forwarding in /etc/sysctl.conf by removing the hash mark from the front of the line:
```
net.ipv4.ip_forward=1
```
Also make sure iptables has forwarding enabled with "/sbin/iptables -L -nv".  You can set it globally as a "policy" with
```
/sbin/iptables -P FORWARD ACCEPT
```

---

### Post by brian131 on 2016-06-23
Nope.  I tried telneting in from the server itself and remotely. 5060 opens, but the alternate port does not. What's stranger is that local addresses can connect to 5060, so it has to be the forwarding that isn't working. Yes, I confirmed both of the above settings are there.

---

### Post by SeijiSensei on 2016-06-24
Let's try another forwarding method.

Remove the PREROUTING rule from the iptables ruleset.  Now install xinetd with "sudo apt-get install xinetd".  In the directory /etc/xinetd.d/ create a file named "asterisk" (or any other name you want) with this content:
```

service astforward
{
        disable         = no
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        bind            = 0.0.0.0
        log_on_failure  += USERID
        redirect        = ip.addr.of.server 5060
}

```
with the server's IP address in the redirect line.

Now edit the file /etc/services and create a new service called astforward with a line:
```
astforward    15060/tcp      # forwarder to asterisk
```

Restart xinetd with "sudo service xinetd restart" and see what happens when you connect to port 15060.

---

