---
title: "Curious case of Ubuntu Server coming back online automatically"
date: 2023-02-22
forum: Networking &amp; Wireless
---

### Post by biswas-pinaki1708 on 2023-02-22
Here is what happened,

Approximately at 2023-02-17 09:57:13 UTC my Ubuntu server went offline. I got this timestamp from when the server disconnected from VPN (vpn logs).
The server automatically came back online on Mon Feb 20 01:32 UTC, 3 days later. Got this timestamp from $last reboot. Also $uptime backs it up. 

Could someone point me to the logs to check why this happened? I can post the required logs here.
When the server went offline, I could access other devices in the network so connectivity was ok.

System setup-
Ubuntu Server - 5.15.0-60-generic #66-Ubuntu SMP 
Remote access via SSH and Teamviewer(commandline only)
lightdm and xfce installed but running in default on [COLOR=#000000][FONT=&quot]multi-user mode.[/FONT][/COLOR]
Remote only with no physical access. Has 24X7 power backup.
I can wake on lan this server via Alexa. Tested OK. I did WOL on the 17th when the system went done and couple of times after that, but no result.
It has AMD hardware watchdog module sp5100_tco loaded. Never tested if it works. Don't know how to. But dmesg shows "sp5100-tco sp5100-tco: initialized. heartbeat=60 sec (nowayout=0)"
Runs few CRON scripts to maintain uptime.
1. Reboots the itself if disconnected from VPN, runs once a day. Never tested via CRON, but bash run works OK.
2. Reboots the router/modem if server can't reach the internet(google), runs once a day. Never tested via CRON, but bash run works OK.

---

### Post by TheFu on 2023-02-23
[https://ubuntu.com/tutorials/viewing-and-monitoring-log-files](https://ubuntu.com/tutorials/viewing-and-monitoring-log-files)
[https://ubuntu.com/server/docs/logging-monitoring-alerting](https://ubuntu.com/server/docs/logging-monitoring-alerting)
[https://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located](https://askubuntu.com/questions/186276/where-are-all-the-major-log-files-located)

I can say I have no interest in looking through full logs, but if you find 10-20 **RELEVANT** lines and post those, I'll look.
My initial guesses are around issues with WoL and the VPN.

---

