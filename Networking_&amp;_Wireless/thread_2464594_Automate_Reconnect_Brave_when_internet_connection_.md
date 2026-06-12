---
title: "Automate Reconnect Brave when internet connection fails"
date: 2021-07-05
forum: Networking &amp; Wireless
---

### Post by zubbs1 on 2021-07-05
I have an internet connection that drops out randomly (long story, 4g home internet in the country, no fix for this until starlink--hopefully).  When it drops, my express vpn connection which loads through the brave browser kills all internet traffic until it reloads, but it times out reconnecting before the internet reconnects.  There is no customization of express vpn, so I was hoping there was a way to do it through relaunching brave.

The vpn will autoconnect on Brave launch.  So I need a workaround.  I don't do anything gracefully, so the most brute force solution is fine.  Is there an easy script that can ping for a connection test and if failed, close and reload Brave?

---

### Post by erind on 2021-07-09
You can write such a script by pinging the connection in regular intervals, say every 3 minutes, and if there's no connection restart Brave. If Brave can be started from the command line then the script would be an easy one.

---

