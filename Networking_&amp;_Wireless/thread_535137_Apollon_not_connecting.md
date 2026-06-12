---
title: "Apollon not connecting"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by bluefightingcat on 2007-08-26
Hi,

I recently installed Apollon and everything seems to have installed correctly. The problem is now that Apollon never manages to connect to any of the networks. This is what my giFT log file shows:

> [11:41:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 66.25.106.165:1445, load: 50%
[11:41:13] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[11:41:17] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.21.235.64:3495
[11:41:17] FastTrack: fst_session.c:128(fst_session_connect): connecting to 216.228.179.140:2978, load: 50%
[11:41:17] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[11:41:21] OpenFT: ft_conn.c:324(keep_alive): kept 0 connections alive
[11:41:21] OpenFT: ft_conn.c:351(acquire_new_stuff): seeking more parents...
[11:41:21] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 68.14.158.75:1281
[11:41:23] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 62.166.74.108:1214
[11:41:23] FastTrack: fst_session.c:128(fst_session_connect): connecting to 62.21.217.226:3968, load: 50%
[11:41:23] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 130.184.23.142:1268
[11:41:23] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.47.15.140:3836, load: 50%
[11:41:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.122.53.52:1400
[11:41:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.254.138.136:3065, load: 50%
[11:41:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 66.25.106.165:1445
[11:41:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.168.232.145:1204, load: 50%
[11:41:32] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 216.228.179.140:2978
[11:41:32] FastTrack: fst_session.c:128(fst_session_connect): connecting to 217.121.228.142:3316, load: 50%
[11:41:37] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[11:41:38] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 62.21.217.226:3968
[11:41:38] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.32.104.163:3576, load: 50%
[11:41:38] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[11:41:38] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.47.15.140:3836
[11:41:38] FastTrack: fst_session.c:128(fst_session_connect): connecting to 209.168.158.169:1798, load: 50%
[11:41:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.254.138.136:3065
[11:41:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.187.197.188:3292, load: 50%
[11:41:39] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.168.232.145:1204
[11:41:39] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.220.97.187:2426, load: 50%
[11:41:47] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 217.121.228.142:3316
[11:41:47] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.12.183.36:1730, load: 50%
[11:41:47] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.12.183.36:1730
[11:41:47] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.209.86.98:1308, load: 50%
[11:41:53] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.32.104.163:3576
[11:41:53] FastTrack: fst_session.c:128(fst_session_connect): connecting to 12.221.16.227:2852, load: 50%
[11:41:53] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 209.168.158.169:1798
[11:41:53] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.226.251.190:3534, load: 50%
[11:41:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.187.197.188:3292
[11:41:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 84.24.141.173:3564, load: 50%
[11:41:54] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.220.97.187:2426
[11:41:54] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.9.231.168:2717, load: 50%
[11:41:58] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[11:42:02] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.209.86.98:1308
[11:42:02] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.20.200.187:3726, load: 50%
[11:42:02] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[11:42:08] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 12.221.16.227:2852
[11:42:08] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.128.79.181:1895, load: 50%
[11:42:08] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.226.251.190:3534
[11:42:08] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.202.251.202:3654, load: 50%
[11:42:08] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.128.79.181:1895
[11:42:08] FastTrack: fst_session.c:128(fst_session_connect): connecting to 204.116.81.119:3167, load: 50%
[11:42:08] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 204.116.81.119:3167
[11:42:08] FastTrack: fst_session.c:128(fst_session_connect): connecting to 66.188.213.205:3106, load: 50%
[11:42:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 84.24.141.173:3564
[11:42:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 69.194.197.161:1388, load: 50%
[11:42:09] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.9.231.168:2717
[11:42:09] FastTrack: fst_session.c:128(fst_session_connect): connecting to 68.110.195.48:2336, load: 50%
[11:42:21] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.20.200.187:3726
[11:42:21] FastTrack: fst_session.c:128(fst_session_connect): connecting to 66.65.150.129:2205, load: 50%
[11:42:22] FastTrack: fst_fasttrack.c:285(fst_plugin_discover_callback): discovery cycle complete: 10 pings, 0 pongs, 0 others
[11:42:23] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 24.202.251.202:3654
[11:42:23] FastTrack: fst_session.c:128(fst_session_connect): connecting to 65.97.7.146:2744, load: 50%
[11:42:23] FastTrack: fst_fasttrack.c:229(fst_plugin_connect_next): discovery cycle started with 10 UDP pings
[11:42:23] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 66.188.213.205:3106
[11:42:23] FastTrack: fst_session.c:128(fst_session_connect): connecting to 207.237.214.18:3364, load: 50%
[11:42:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 69.194.197.161:1388
[11:42:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 62.179.216.215:1379, load: 50%
[11:42:24] FastTrack: fst_session.c:164(fst_session_disconnect): disconnected from 68.110.195.48:2336
[11:42:24] FastTrack: fst_session.c:128(fst_session_connect): connecting to 24.93.189.44:1217, load: 50%


Does anybody know what this means?

BFC

---

### Post by ddrichardson on 2007-08-27
Have you forwarded a port for Apollon?

---

### Post by bluefightingcat on 2007-08-27
Hi,

How do I do that exactly? I am not using a firewall. 

BFC

---

### Post by ddrichardson on 2007-08-27
Ports are closed by default in Ubuntu - so in a way you are. Try firestarter to enable a port easily and although very Windows oriented there is a good guide to setting up your router [here]("http://portforward.com/routers.htm").

---

