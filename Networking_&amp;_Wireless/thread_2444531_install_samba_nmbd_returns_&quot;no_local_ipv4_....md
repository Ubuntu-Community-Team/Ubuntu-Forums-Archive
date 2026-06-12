---
title: "install samba nmbd returns &quot;no local ipv4 ... available&quot; with wired ipv4 interface"
date: 2020-05-31
forum: Networking &amp; Wireless
---

### Post by jasonloveslinux on 2020-05-31
Running Ubuntu 18.04 LTS on a DreamCompute instance using their 18.04 LTS image. At 'apt install samba', installation proceeds normally until the script tries to launch the nmbd service. The script stalls for 90 seconds then returns a failure message. /var/log/log.nmbd reports:

```
[COLOR=#000000][FONT=Menlo][2020/05/31 23:27:07.406916,[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]0] ../lib/util/become_daemon.c:135(daemon_status)[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]STATUS=daemon 'nmbd' : No local IPv4 non-loopback interfaces available, waiting for interface ...NOTE: NetBIOS name resolution is not supported for Internet Protocol Version 6 (IPv6).[/FONT][/COLOR]
```


journalctl -xe reports:

```
[COLOR=#000000][FONT=Menlo]Jun 01 00:10:14 mydevserver systemd[1]: Starting Samba NMB Daemon...[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]-- Subject: Unit nmbd.service has begun start-up[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-- Defined-By: systemd[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-- Support: http://www.ubuntu.com/support[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-- [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-- Unit nmbd.service has begun starting up.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jun 01 00:11:44 mydevserver systemd[1]: **nmbd.service: Start operation timed out. Terminating.**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jun 01 00:11:44 mydevserver systemd[1]: **nmbd.service: Failed with result 'timeout'.**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jun 01 00:11:44 mydevserver systemd[1]: [COLOR=#B42419]**Failed to start Samba NMB Daemon.**[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-- Subject: Unit nmbd.service has failed[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-- Defined-By: systemd[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-- Support: http://www.ubuntu.com/support[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-- [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-- Unit nmbd.service has failed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-- [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]-- The result is RESULT.[/FONT][/COLOR]
```


With ifconfig, I have confirmed I have a normal IPv4 interface with broadcast that is not loopback:

```
[COLOR=#000000][FONT=Menlo]ens3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]mtu 8900[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]inet [redacted]  netmask [redacted]  broadcast [redacted][/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]inet6 [redacted]  prefixlen 64  scopeid 0x20<link>[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]inet6 [redacted]  prefixlen 64  scopeid 0x0<global>[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]ether [redacted]  txqueuelen 1000  (Ethernet)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RX packets 1254009  bytes 93626989 (93.6 MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]RX errors 0  dropped 2072  overruns 0  frame 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]TX packets 27626  bytes 38604933 (38.6 MB)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/FONT][/COLOR]
```


I have confirmed the problem is NOT:

[LIST]
[*]a race condition between samba and the network interface. This error happens during installation and live troubleshooting.
[*]a smb.conf problem. testparm returns "Loaded services file OK."
[*]a general network interface problem. I am connected to my server over ssh with certificate. The preferred interface has IPv4, has broadcast, and is not loopback.
[*]a reboot or reinstall problem. I have methodically tested install-reboot-check-remove-purge-samba-*-autoremove-reboot-install. This problem is reproduce-able for me.
[/LIST]

This is a well behaved dev server. I have installed nginx, node, wireguard, and a few misc packages without any trouble. I have not tweaked or patched any issues. This box is about as vanilla as you can get. I have reached out DreamCompute, but they generally don't troubleshoot your box for you. The DreamComputer KB has no information regarding samba, suggesting that the DreamComputer image of LTS 18.04 has **not** been customized.

Rather than just ask you for answers, I would like to grow my troubleshooting skills. Given the above information, **what do you think my smartest approach to troubleshooting should be?** That is, now that I have familiarized myself with various documentation and other troubleshooting threads on similar issues, are there any obvious or subtle points that I might need to understand? Are there long running gotchas that I wouldn't know about unless I knew what to look for?

---

