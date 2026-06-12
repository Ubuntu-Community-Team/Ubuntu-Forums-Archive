---
title: "[SOLVED] Help With Port Forwarding"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by DGortze380 on 2008-08-13
I'm not sure what I'm doing wrong here. For a number of reasons this is what I'm trying to set up:

1) dyndns host (can't test until everything else works i don't think)
     to
2) d-link router (see screen shot)
3) forward incoming ssh (sftp) traffic on port 80 to port 22 on a local machine

seems simple, thought it would be relatively easy but I can't get it running.
ssh works correctly on the end machine. I can connect using it's ip over the local network

ex.
```

ssh user@192.168.0.110

```

but when I tried to test the port forwarding I get this error:

ex. 
```

ssh -p 80 user@192.168.0.1
ssh_exchange_identification: Connection closed by remote host

```

Anyone have any ideas on why this port forwarding wouldn't work? Can I not test port forwarding locally?

---

### Post by jimv on 2008-08-13
Port forwarding doesn't work from the router's LAN address (the 192.168.0.1 address).  You need to use the router's WAN address (the one it gets from your ISP) in your SSH command.  Uou should be able to get that address from the Status page on your router.

You can also get the WAN IP by going to [http://whatismyip.com/](http://whatismyip.com/)

So your command will be:

ssh you@WAN-address -p 80

---

### Post by DGortze380 on 2008-08-13
> **jimv said:**
> Port forwarding doesn't work from the router's LAN address (the 192.168.0.1 address).  You need to use the router's WAN address (the one it gets from your ISP) in your SSH command.  Uou should be able to get that address from the Status page on your router.

You can also get the WAN IP by going to [http://whatismyip.com/](http://whatismyip.com/)

So your command will be:

ssh you@WAN-address -p 80

ok, sorry about that. tried two different things.

```

ssh user@mysite.dyndns.org -p 80

ssh user@my-wan -p 80

```

Both times got this back (edited the ip for the post):

ssh: connect to host 76.119.***.*** port 80: Operation timed out

dyndns is working, I am able to log into my router via mysite.dyndns.org
Any other ideas on why this wouldn't work??

---

### Post by DGortze380 on 2008-08-13
stupid mistake. forwarding port 22 on the router and trying to connect on port 80... definitely not going to work. left -p 80 out of the command and it works fine.

---

