---
title: "Monitoring network traffic by process/program name"
date: 2019-09-12
forum: Networking &amp; Wireless
---

### Post by hikariws on 2019-09-12
I've been searching for a tool that does it and couldn't find any yet.

I'm using YAmon on my OpenWRT router, with it I'm able to monitor internet traffic for each device on my LAN. It happens that 99% of my traffic comes from my Ubuntu server, as I have Transmission and CrashPlan on it.

I'm looking then to a tool to run on this server, that allows me to monitor traffic by program (full path) name. If possible, include too parameter it received when executed, as they all run as daemon.

I'd need to exclude inbound and outbound connections on LAN, as this server does a lot of traffic with my NAS too.

Could anybody suggest me? Or is it that hard to monitor traffic by process?

---

### Post by SeijiSensei on 2019-09-12
How about [https://www.tecmint.com/nethogs-monitor-per-process-network-bandwidth-usage-in-real-time/](https://www.tecmint.com/nethogs-monitor-per-process-network-bandwidth-usage-in-real-time/)

I haven't used it (I don't really care about traffic on my home network), so I can't answer your other questions.

---

### Post by hikariws on 2019-09-12
This seems very interesting! I'm gonna look for some WebUI for it or some way to persist its data, tnx!

---

