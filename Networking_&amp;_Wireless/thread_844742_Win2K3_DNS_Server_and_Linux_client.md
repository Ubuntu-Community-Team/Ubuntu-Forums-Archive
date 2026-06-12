---
title: "Win2K3 DNS Server and Linux client"
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by DoubleEweAreEx on 2008-06-29
Hi

I have a Windows 2003 R2 Domain and I am trying to join Ubuntu 8.04 client.
I seem to be falling down at the first hurdle as I can not ping via dns.
I can ping IP's and hosts that are in the hosts file.
The client has an entry for the DNS server in the /etc/resolv.conf file.

I suspect that it is a problem with the Win2K3 server. 
Would anyone know where to start looking?
Cheers!

Damo

---

### Post by zooper on 2008-06-30
Hi,

I don't think there is a problem with your 2k3 server.
I suppose there is a dhcp server on the network . The server should provide you with a domainname, (ex. domain.local) and update your /etc/resolv.conf with the domainname. 

What you should do is take a look in your /etc/resolv.conf, look what the search parameter says. If your local domain is domain.local, it should be:
"search domain.local"

```

### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5212
#
### END INFO

**search domain.local**


nameserver <your nameserver>

```

If you type the command "ping somemachine", you computer will ask the DNS: whois somemachine.domain.local.

And if you want to join a AD domain, you should take a look at a package called "likewise". You can find it in the resp.

---

### Post by DoubleEweAreEx on 2008-06-30
Ahh, I will add the search for domain line to the resolv.conf file.
However I think I still might have an issue with DNS as I can not pick the name of the DC via DNS.
Do I need to enable anything in DNS to allow non windows 2000+ clients to connect to it?

---

