---
title: "&quot;Routing&quot; DNS queries to different servers?"
date: 2013-11-13
forum: Networking &amp; Wireless
---

### Post by olivier-godart-gmail on 2013-11-13
Hi there,

I have setup my VPN client with proper routing so that my default route remains the internet, and only the addresses in my company internal network are routed through the VPN.
This is working correctly, but however, I didn't find a way to do the same with DNS queries.
I would like to have a default DNS server, but all queries to *.mycompany.com and *.mycompanycorp.com and a few other domains should be directed to the DNS server provided by the VPN.

Is there a way to do that? It's probably possible using bind but I'm not familiar with it. (I didn't find a way to do it with dnsmasq, dnscache or resolvconf.)

Thanks

---

### Post by olivier-godart-gmail on 2013-11-13
Actually, I think I can find a way to do that using the --server option of dnsmasq. I just have to find a way to do that automatically with network-manager

---

### Post by SeijiSensei on 2013-11-13
If you are running a BIND server, you can use forwarders for specific domains.  In named.conf you would have entries like

```

zone "mycompany.com" {
     type forward;
     forward only;
     forwarders { ip.addr.of.dnsserver };
};

```

Then queries sent to this server will be resolved against the server at "ip.addr.of.dnsserver".

---

