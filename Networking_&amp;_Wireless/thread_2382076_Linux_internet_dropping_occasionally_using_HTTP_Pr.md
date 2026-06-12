---
title: "Linux internet dropping occasionally using HTTP Proxy?"
date: 2018-01-08
forum: Networking &amp; Wireless
---

### Post by samanx on 2018-01-08
In order to use internet at my university campus I need to set an HTTP Proxy which under Windows 10 works *ok without latency and connection problems unless (*I say ok because at peak hour everything is painfully slow).
The problem is on linux where the speed is negatively impacted in relation to windows 10 and has terrible latency, waiting 4-6 seconds just for initial DNS lookup.
Sometimes the page doesn't load at all and I have to refresh 2-3 times.
If I open 3-4 tabs under chrome and the dns resolves the 5 tab isn't loading at all (Waiting for socket...).


INFO:
- http_proxy: department.university.com
- proxy_port: 8080


```
 ~/eq $ sudo systemctl status NetworkManager.service


&#9679; NetworkManager.service - Network Manager
   Loaded: loaded (/usr/lib/systemd/system/NetworkManager.service; enabled; vendor preset: disabled)
  Drop-In: /usr/lib/systemd/system/NetworkManager.service.d
           &#9492;&#9472;NetworkManager-ovs.conf
   Active: active (running) since Mon 2018-01-08 16:44:27 EET; 7h ago
     Docs: man:NetworkManager(8)
 Main PID: 434 (NetworkManager)
    Tasks: 11 (limit: 4915)
   CGroup: /system.slice/NetworkManager.service
           &#9500;&#9472; 434 /usr/bin/NetworkManager --no-daemon
           &#9500;&#9472;1803 /usr/lib/nm-pptp-service --bus-name org.freedesktop.NetworkManager.pptp.Connection_40
           &#9500;&#9472;1807 /sbin/pppd pty /sbin/pptp 192.168.128.3 --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-1803 ipparam nm-pptp-service-1803 nodetach lock usepeerdns noipdefault nodefaultroute noauth refuse-eap refuse-pap refuse-ch
           &#9500;&#9472;1810 /sbin/pptp 192.168.128.3 --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-1803
           &#9492;&#9472;1820 /sbin/pptp 192.168.128.3 --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-1803


Jan 09 00:09:13 xedo NetworkManager[434]: <info>  [1515449353.2755] connectivity: (wlan0) timed out
Jan 09 00:09:15 xedo pptp[1820]: nm-pptp-service-1803 log[logecho:pptp_ctrl.c:719]: Echo Reply received.
Jan 09 00:10:15 xedo pptp[1820]: nm-pptp-service-1803 log[logecho:pptp_ctrl.c:719]: Echo Reply received.
Jan 09 00:11:15 xedo pptp[1820]: nm-pptp-service-1803 log[logecho:pptp_ctrl.c:719]: Echo Reply received.
Jan 09 00:12:15 xedo pptp[1820]: nm-pptp-service-1803 log[logecho:pptp_ctrl.c:719]: Echo Reply received.
Jan 09 00:12:15 xedo pptp[1820]: nm-pptp-service-1803 log[logecho:pptp_ctrl.c:721]: no more Echo Reply/Request packets will be reported.
Jan 09 00:14:13 xedo NetworkManager[434]: <info>  [1515449653.2765] connectivity: (wlan0) timed out
Jan 09 00:19:13 xedo NetworkManager[434]: <info>  [1515449953.2795] connectivity: (wlan0) timed out
Jan 09 00:24:13 xedo NetworkManager[434]: <info>  [1515450253.2789] connectivity: (wlan0) timed out 
Jan 09 00:29:13 xedo NetworkManager[434]: <info> [1515450553.2774] connectivity: (wlan0) timed out
```


I'm on Ubuntu with Gnome (previously xfce4 but a bit hard to set/unset proxy).


Is there any way I can solve those problems? I disabled ipv6 because of some errors in dmesg.

---

### Post by DuckHook on 2018-01-08
What advice have your campus network admins given you?

---

