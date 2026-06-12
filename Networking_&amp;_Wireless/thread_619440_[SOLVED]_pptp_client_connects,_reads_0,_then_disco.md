---
title: "[SOLVED] pptp client connects, reads 0, then disconnects"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by cmnorton on 2007-11-21
My pptp client connects, then disconnects. I have tried a connect-delay in /etc/ppp/options.pptp, and have the settings I have seen posted in these forums. I would appreciate any ideas on where to look or what to try next.

Please note that "xx" is used to substitute for the real vpn address. There is a real address in the real script, and this vpn is reachable from an XP system using the same wireless router.

Is it possible that Ubuntu is interacting with my Linksys router differently than Windows XP that would prevent the VPN connection from completing?

---

### Post by J1m on 2007-11-23
Hi cmnorton,

I am assuming you are using the netwrok-manager-pptp applet to configure your vpn settings?

The settings I had to use were different from all the settings that people had posted on the forums.

It looks like your client and server can communicate initially but then the server breaks the connection.

I don't know whether its your authentication, compression or encryption - but I'll bet changing the settings will get it to work.

Try messing with authentication first to see if you can produce different log messages - then move on to compression and encryption.

I had no idea why my PPTP client could not keep a connection - googling the log messages was producing very vague results.  Fiddle with the settings - try different combinations - regardless of what settings others have used - thats how I got mine working.

Good Luck

J1m

---

### Post by cmnorton on 2007-11-23
Yes, I did use Network Manager to create the settings. I will keep fiddling with this, and then post the results.

---

### Post by cmnorton on 2007-12-01
The pptp settings in the various Ubuntu forums and encouraging fiddling with those settings are all very good advice, and I would not have gotten as far as this original note without following that advice. 

I am now connecting with pptp VPN, because out of desperation, I gave up on the Acer Travelmate 630's built-in wireless card and went with a newer Linksys wireless card. When I was sitting right next to the wireless router and could not connect over wireless without using VPN, but could being plugged into the router, I knew something was terribly wrong.

---

