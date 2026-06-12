---
title: "PPP connection keeps dropping"
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by Tixer on 2008-09-14
I use PPPoE on my server, which also has a link to my desktop through a router (hence how I'm diagnosing it.) The problem is that the ppp connection isn't redialing whenever something goes wrong with the modem, and I'd like to fix it.

Here is my config file:

# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
mtu 1484
multilink
maxfail 0
holdoff 10
plugin rp-pppoe.so eth1
user [redacted]

By the way, eth1 is the dedicated ppp port, router traffic is on eth0.

Also, on another note, I'd like to get rid of the router and get internet straight from my server. I only have 100mbits with the router, whereas both computers have gigabit. Bonus points to whoever can answer that.

---

### Post by lswb on 2008-09-14
If I could suggest, how about finding out what is causing the modem to disconnect? I'm assuming this is pppoe to a dsl modem. Some dsl modems can be configured to drop the connection when there is no traffic, or to maintain a constant connection (usually the latter would be desired) What do you need to do to reconnect when "something goes wrong with the modem"?

Another suggestion, modern routers can do pppoe and act as a dhcp server. Have you considered configuring the router to connect to the modem? The computers would then simply connect to the router using tcp/ip. If your server requires outside access the router would need NAT set up to send requests to it.

On the last item, internet connection sharing is feasible on the server if it has 2 or more ethernet adapters, but I would not be concerned with the 100mbs/1Gb issue. Since no DSL connection can get anywhere near 100mbs anyway (a few mbs is common), you would not gain any internet connection speed. (Though if you often transfer large files between the server and the other local computer, it might be useful)

---

### Post by Tixer on 2008-09-14
The modem is disconnecting as a result of failure, possibly from a low SnR, or due to a storm. It isn't due to improper setup. The router automatically keeps redialing until it connects again, so I don't see the problem on my desktop. However, my server doesn't redial, so I need to ssh in, run pon dsl-provider, then check ifconfig, make sure it worked, and then run ddclient again.

The reason behind the direct line to the modem is due to my ISP trying to throttle torrents. All you need to defeat it is a multilink connection, which none of the routers here support. Rather than buying a new one, I just installed a WebUI to Azureus and use my server to torrent.

As for the connection sharing, I'm aware I only have a 5 meg DSL connection. However, as stated above, I'm using this to torrent, and so occasionally I need to push several hundred gigs at a time. I also stated it has two network cards, one for pppoe and one to the router (which only has my computer).

---

### Post by lswb on 2008-09-14
So pppd on the server is exiting completely before the modem can reestablish the DSL link? From the options you posted it seems like it should just keep trying every 10 seconds but there are so many options for pppd.... When you ssh into the server is the pppd process still running?

As a dirty work around, you may be able to do something with a script in the
/etc/ppp/ip-down.d directory or perhaps a cron job that periodically checks the connection and runs pppd if it is down.

If you search for "internet connection sharing" you can find threads that explain how to do away with the router for your setup. I'm not familair with the details of that, you will have to install dhcp server on your server and bind it to the ethernet port that is connected to the other computer, and may need a crossover cable; some ethernet adapters can automatically sense and connect without the crossover cable.

---

