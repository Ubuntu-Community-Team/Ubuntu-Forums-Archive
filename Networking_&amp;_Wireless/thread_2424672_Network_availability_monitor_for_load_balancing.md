---
title: "Network availability monitor for load balancing"
date: 2019-08-12
forum: Networking &amp; Wireless
---

### Post by hikariws on 2019-08-12
Hello everybody!


I know a bit of linux for a decade and a few years ago I got a NAS which gave me the opportunity to use linux at home. Now I decided to buy a small PC and install Ubuntu on it, and get more used on linux as I move from my Windows server to it some services like Transmission, Tor bridge relay, Squid, OpenDNS and no-ip updaters, etc.


It's being easier than I expect, but some stuff is trickier. One of them is PRTG, which I use to monitor internet availability.


I've googled and found some alternative candidates, but I'd like to try to go further. I have 2 IPSs load balanced by a Cisco RV340. I'm looking for some way to distinctly monitor each of them.


The tricky part is that they don't have (ASAIK) any host I could ping from inside their intranet that's unavailable on the internet. I'd need to find a way to know if a ping is going from the right ISP and not the other.


In example, a given IP is reached in 3 hops from one ISP, and 10 hops from the other. So, if I make some tool ping every minute and for 5 minutes it never gets there in 3 hops, I know that ISP is down.


Anybody knows any tool that would do that, or has any idea of how I could accomplish it?

---

### Post by &amp;wP*!) on 2019-08-14
**ping -i <interval>** (in seconds) sets the time between two consecutive pings combined with **-c <number of pings>** and **-W timeout**
Use a timer which calls your ping in the intervals you want. You can use cron/anacron or systemd timers.
And the output to be redirected to a log and process the stdout/stderr (For systemd timer, ExecStopPost attributee in unit file described in the manual system.service(5) might help). The TTL value coming from ping (in stdout/stderr) could be evaluated as well.

Could these tools help you?

---

### Post by hikariws on 2019-08-14
Thanks!

I dediced to use hc-ping.com for monitoring, but I may change because it doesn't seem to have any carts or statistics to see availability over time, it's oriented on notifying us if any monitor goes down. Any suggestion would be greatly appreciated.

Anyway, I used the following code

```

if fping -c 1 -t 7 187.115.215.xxx &> /dev/null
then
   curl -s https://hc-ping.com/123456789 &> /dev/null
fi

```

It uses fping into the closest host on one of my ISPs, and gives 7s for timeout. If it doesn't timeout, its WAN was used therefore it's up.

Sadly my RV340 gives precedence to WAN1 for pings, and all pings and trace routes I run always go to WAN1 unless it's down, so I can't test ISP2.

---

