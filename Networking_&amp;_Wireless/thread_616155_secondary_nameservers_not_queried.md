---
title: "secondary nameservers not queried?"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by bretticus on 2007-11-17
Hi,

I am a road warrior with a openvpn account to my company network. My company's server config pushes dns servers to my /etc/resolv.conf file (via /etc/openvpn/tun.up.sh.) I also maintain my very own caching dns server at home to which I have added some home network aliases. My problem is that when tun.up.sh overwrites resolv.conf, my company dns servers are listed before my default nameserver. And when I try to resolve my home dns aliases, I get nxdomain. Using a simple dig, I can see that the dns server used is the first one on the list (my company's.) Which confuses me since a "$ man resolver" shows:

>  name servers
              may  be  listed,  one per keyword.  **If there are multiple servers, the resolver library queries them in the order listed**.  If no nameserver
              entries are present, the default is to use the name server on the local machine.  (The algorithm used is to [B]try a name server, and  if  the
              query  times  out,  try  the next, until out of name servers, then repeat trying all the name servers until a maximum number of retries are
              made[/B].)

I attempted to alter my tun.up.sh file to make my current (default) nameserver be listed first..you guessed it...now my internal company aliases do not resolve.

Can anyone point me in the right direction?:confused:

---

### Post by jetsam on 2007-11-21
I'm fairly new to networking, so read this with that in mind, but I did some puzzling and googling over this one, and every time I thought I might be getting close to an idea, I re-read your description of the situation and found a new layer of complexity there that would be a roadblock.  

Regarding the not falling back to the secondary nameserver, I'm thinking that nxdomain counts as a response from the DNS server, different from a timeout, so the resolver never rolls over to the next nameserver.

Have you considered just adding your home network hostnames to your hosts file in /etc/hosts?  Not a very elegant solution, but I'm pretty sure it would work...

---

