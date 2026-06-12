---
title: "Help needed for wifi hotspot"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by walfroy on 2008-10-07
Hello,
I have to set a wifi hotspot in the hotel I work for.

I have :
- Ubuntu server with 2 eth cards
- some wifi access point
- router that shares the connection with my local network

I need :

- Client need to authentify to get access to internet
- Changing the password must be noob-friendly (prompted script or web page)
- All connections need to be logged (MAC adresses and pages visited)

At first I started by setting a server (Ubuntu) with dhcp3 (logs MAC vs IP), squid (logs activity), bind.
It works wonders when client PC points to the proxy IP and port but won't work with redirection.
I've been told today that it can NOT work with redirection ...

I'm a bit pissed because 95% of the work is done ...

I'm thinking either find a firewall that supplies the login part or make a web page that will redirect to the web upon login.

The thing is I don't really have the time to learn and to developp such a thing.

If someone has an idea, i'm getting pretty deseperate.

---

### Post by walfroy on 2008-10-07
Can someone please help ?

---

