---
title: "netfilter-persistent and iptables"
date: 2020-05-26
forum: Networking &amp; Wireless
---

### Post by catadetest on 2020-05-26
[FONT=arial]Dear community,[/FONT]

[COLOR=#242729][FONT=Arial]Desiring to use iptables on ubuntu 18.04, I removed the ufw and installed iptables-persistent netfilter-persistent. Edited the /etc/iptables/rules.v4 and tried to start the netfilter-persistent service. It's working, but the last exit status is not 0, probably something's wrong when stopping the service[/FONT][/COLOR][FONT=arial]

[/FONT]
[FONT=system][FONT=arial]iptables -nL output:[/FONT]
[/FONT]```
[FONT=system]
Chain INPUT (policy DROP)[/FONT]
[FONT=system]target     prot opt source               destination         [/FONT]
[FONT=system]ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED[/FONT]
[FONT=system]ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           [/FONT]
[FONT=system]ACCEPT     tcp  --  192.168.1.129        0.0.0.0/0            tcp dpt:22
[/FONT][FONT=system]Chain FORWARD (policy ACCEPT)[/FONT]
[FONT=system]target     prot opt source               destination         [/FONT]
[FONT=system]
[/FONT]
[FONT=system]Chain OUTPUT (policy ACCEPT)[/FONT]
[FONT=system]target     prot opt source               destination      [/FONT]   

```

[FONT=arial]status of the service:
[/FONT]```

[FONT=system]root@my-server:/etc/iptables# systemctl status netfilter-persistent[/FONT]
[FONT=system]&#9679; netfilter-persistent.service - netfilter persistent configuration[/FONT]
[FONT=system]   Loaded: loaded (/lib/systemd/system/netfilter-persistent.service; enabled; vendor preset: enabled)[/FONT]
[FONT=system]   Active: active (exited) since Tue 2020-05-26 12:39:17 UTC; 19min ago[/FONT]
[FONT=system]  Process: 4402 ExecStop=/usr/sbin/netfilter-persistent stop (code=exited, status=1/FAILURE)[/FONT]
[FONT=system]  Process: 4408 ExecStart=/usr/sbin/netfilter-persistent start (code=exited, status=0/SUCCESS)[/FONT]
[FONT=system] Main PID: 4408 (code=exited, status=0/SUCCESS)[/FONT]
[FONT=system]
[/FONT]
[FONT=system]May 26 12:39:17 my-webserver systemd[1]: Starting netfilter persistent configuration...[/FONT]
[FONT=system]May 26 12:39:17 my-webserver netfilter-persistent[4408]: run-parts: executing /usr/share/netfilter-persistent/plugins.d/15-ip4tables start[/FONT]
[FONT=system]May 26 12:39:17 my-webserver netfilter-persistent[4408]: run-parts: executing /usr/share/netfilter-persistent/plugins.d/25-ip6tables start[/FONT]
[FONT=system]May 26 12:39:17 my-webserver systemd[1]: Started netfilter persistent configuration.[/FONT]

```

[FONT=arial]journalctl -e -u netfilter-persistent.service[/FONT]
[FONT=system]
[/FONT]```
[FONT=system]
May 26 12:39:01 my-webserver systemd[1]: Started netfilter persistent configuration.[/FONT]
[FONT=system]May 26 12:39:17 my-webserver systemd[1]: Stopping netfilter persistent configuration...[/FONT]
[FONT=system]May 26 12:39:17 my-webserver netfilter-persistent[4402]: Automatic flush disabled; use '/usr/sbin/netfilter-persistent flush'[/FONT]
[FONT=system]May 26 12:39:17 my-webserver systemd[1]: netfilter-persistent.service: Control process exited, code=exited status=1[/FONT]
[FONT=system]May 26 12:39:17 my-webserver systemd[1]: netfilter-persistent.service: Failed with result 'exit-code'.[/FONT]
[FONT=system]May 26 12:39:17 my-webserver systemd[1]: Stopped netfilter persistent configuration.[/FONT]
[FONT=system]May 26 12:39:17 my-webserver systemd[1]: Starting netfilter persistent configuration...[/FONT]
[FONT=system]May 26 12:39:17 my-webserver netfilter-persistent[4408]: run-parts: executing /usr/share/netfilter-persistent/plugins.d/15-ip4tables start[/FONT]
[FONT=system]May 26 12:39:17 my-webserver netfilter-persistent[4408]: run-parts: executing /usr/share/netfilter-persistent/plugins.d/25-ip6tables start[/FONT]
[FONT=system]May 26 12:39:17 my-webserver systemd[1]: Started netfilter persistent configuration.
[/FONT]
```

---

