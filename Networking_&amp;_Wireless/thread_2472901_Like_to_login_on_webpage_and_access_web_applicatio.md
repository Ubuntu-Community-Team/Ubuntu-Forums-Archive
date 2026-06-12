---
title: "Like to login on webpage and access web application on my network"
date: 2022-03-16
forum: Networking &amp; Wireless
---

### Post by cazz on 2022-03-16
Hi
Is it possible to install a linux server that I can access from outside my network and access web applikations that is on my network?
I do not like to enable to many port on my firewall.

Example I have some ubuntu server that run cockpit and it use port 9090 so I hope I can login on one site and then access my ubuntu servers?

---

### Post by TheFu on 2022-03-16
> **cazz said:**
> Hi
Is it possible to install a linux server that I can access from outside my network and access web applikations that is on my network?

Yes. Use an ssh tunnel or an ssh SOCKS5 proxy.  I've posted a little script just for that in these forums a few times, though not recently.

---

### Post by cazz on 2022-03-16
Thanks for the replay
Hmm have google a little and does look nice but not sure if I can get it to work like I want to do.
I apologize if there was a misunderstanding but was a bit stressed when I wrote the question but now have more time to explain what I am looking for

My idea is like Apache Guacamole but instead of RDP/VNC/SSH I like to access HTTP and HTTPS application.
So I login on a webpage at my place and then go to a HTTP/HTTPS address that is on my local network.

---

### Post by TheFu on 2022-03-16
> **cazz said:**
>  My idea is like Apache Guacamole but instead of RDP/VNC/SSH I like to access HTTP and HTTPS application.
So I login on a webpage at my place and then go to a HTTP/HTTPS address that is on my local network.

I looked at Guacamole years ago. Didn't like the architecture and security problems that architecture caused.
Using a SOCKS proxy over ssh will provide exactly the type of access you seek.

When I'm traveling and don't want to connect back home using a full VPN, say I just need browser access to my internal LAN websites (it actually works for external websites too), then I run my proxy script, which launches a browser instance with the command line option to use a specific proxy. From that point, I have full access to all my LAN webapps as though I'm on the LAN. The transfers are sent through the ssh tunnel to my laptop. Works for nextcloud, calibre, plex, jellyfin, anything using http or https protocols.  Try it. Should take 30 seconds.  You'll want any webserver hostnames in your local /etc/hosts file so the lookups work without leaking DNS queries. That's about the only caveat I know.

People don't use ssh-based connections nearly enough when they actually care about security.  ssh is authenticated network access. HTTPS isn't really security. It is just a point-to-point encrypted tunnel, but without network validated access.

---

