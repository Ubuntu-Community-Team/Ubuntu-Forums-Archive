---
title: "Ubuntu Server 20 - How to assign a domain name?"
date: 2021-01-12
forum: Networking &amp; Wireless
---

### Post by ryan170 on 2021-01-12
Hello,

I've recently bought an Intel NUC to use as a media server, and I would like to assign a domain name to it in order to make accessing the programs (plex, sonarr, radarr, etc.) easy. I have a domain name that I bought though namecheap.com. It's currently hosted by Bluehost (using Bluehost's nameservers), but I want the domain to be hosted by my NUC so I can go to domain.com:32400 and access plex, regardless of its IP address.

I've followed the instructions here: [https://linuxconfig.org/how-to-change-fqdn-domain-name-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-change-fqdn-domain-name-on-ubuntu-20-04-focal-fossa-linux) but I haven't noticed a change. Maybe it takes some time for the DNS to propagate. Or maybe I'm not doing something correct.

Do I need to remove the Bluehost nameservers from the Namecheap cpanel? Do I need to replace them with anything? Is there something else I should be doing, or do I just wait a few hours for the DNS to propagate and try the webpage again?

Thanks!

---

### Post by SeijiSensei on 2021-01-12
Do you want to access this server from its public address? Seems like a bad idea to me from a security perspective. At a minimum, run plex on a different port than its default. 

I assume this machine has firewalling and only allows access to a very limited number of ports.

It doesn't matter where your DNS is hosted as long as the records are correct. You would need an A record that points to the server. The link you posted only covers how to set the FQDN on the server itself. It has nothing to do with DNS.

When I make changes to DNS, I check with Google's server at 8.8.8.8. It usually updates pretty quickly.
```
host myserver.domain.name 8.8.8.8
```
will return the address for myserver.domain.name on Google's primary nameserver.

---

