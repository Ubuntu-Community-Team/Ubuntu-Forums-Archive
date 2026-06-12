---
title: "PPP over null modem cable between two raspberry pis"
date: 2022-09-16
forum: Networking &amp; Wireless
---

### Post by div111 on 2022-09-16
[COLOR=#232629][FONT=-apple-system]I am trying to establish ppp (point-to-point protocol) between two raspberry pis. Both are configured for a headless setup and have ubuntu server 22.04.1 LTS running. I have connected 3 wires between the two pis. Tx, Rx and GND. 
I followed this link : [https://tldp.org/HOWTO/PPP-HOWTO/direct.html](https://tldp.org/HOWTO/PPP-HOWTO/direct.html) and assigned a local IP and a remote IP, I am unable to ping from local machine to the remote IP. My understanding is that, after running the pppd command, there should be a ppp0 interface established. This is not happening in my case. Any idea where I might have gone wrong?[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Thanks! 
Divya[/FONT][/COLOR]

---

### Post by SeijiSensei on 2022-09-16
It's been many years since I've done this, but my first suggestion is to look at the logs. pppd might log to /var/log/syslog or it might use its own log file. Look at your configuration file to see.

Did you use the "setserial" command as that web page indicates? Are both machines set to the same speed? Does that speed match the one in the pppd command line?

I assume you're doing this because you don't have free Ethernet ports?

---

