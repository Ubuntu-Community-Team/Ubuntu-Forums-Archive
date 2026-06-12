---
title: "pptp VPN - many sites won't load"
date: 2005-06-28
forum: Networking &amp; Wireless
---

### Post by /usr/err on 2005-06-28
I use pptp ('pptpconfig' application to be exact) to connect to my work VPN on my laptop from home, and many web sites fail to load on a regular basis.  What happens is if I hit a site with Firefox, I get either "Waiting for <site name>..." or "Transferring data from <site name>..." (more common) and it stays that way forever.  Google, Yahoo and a number of other sites work just fine, but more and more lately I keep trying to follow links off of sites and I end up not being able to connect, so it is frustrating as I usually have to leave my VPN connection up during the day to do SSH sessions and other work-related stuff; breaking the VPN just to go do some quick research on a website (or you know... waste time) is annoying, to say the least.

If I disconnect the VPN connection or I'm actually at the office using the exact same network (just not over VPN anymore), everything works fine, so as far as I can tell, this is a pptp issue, but I have no idea what would be causing it or how to test/resolve it.

Any ideas?

---

### Post by cwaldbieser on 2005-06-28
It sounds like you don't have the route to the VPN configured narrowly enough when you are connected.  When you try to look for a website, it is trying to route through your VPN instead of your Internet connection.

When you are connected to your VPN, run these commands in the terminal and post the output:

```
$ ifconfig -a

$ route
```

---

### Post by /usr/err on 2005-06-29
Thanks for the input, it got me going in the right direction.

I played around with 'pptpconfig' a bit and was able to get it to work.  Just in case anyone else has a similar problem, here is what I did:

- Server tab: setup basic VPN info (server: ip/hostname of pptp server, username, etc)

- Routing tab: check 'Client to LAN' box, then click 'Edit Network Routes...' button and 'Add' network routes for your VPN network; for instance, internally my company uses 10.0.0.0 addresses, so I added '10.0.0.0/16', and we have a hardware VPN-to-VPN connection from our company to another company for support reasons, so I added that network as well

- click 'Update' on main 'pptpconfig' screen to update the settings

- click 'Start' and hold your mouth just right and it will hopefully work

I'd tried some of this in the past but could never get it to work, I always had to use the Routing option of 'All to Tunnel' or the VPN and local network would not work at all, but apparently I did something right this time as it is now working as I wanted it to originally (can access VPN network as well as still get to other sites with no issues [so far anyway]).

---

