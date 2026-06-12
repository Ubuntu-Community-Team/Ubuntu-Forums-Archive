---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2018-11-12
forum: Networking &amp; Wireless
---

### Post by dmitrytim on 2018-11-12
installing fprobe (or any other packet) gives error

```
Job for fprobe.service failed. See "systemctl status fprobe.service" and "journalctl -xe" for details.
invoke-rc.d: initscript fprobe, action "start" failed.
dpkg: error processing package fprobe (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 fprobe
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
running  systemctl status fprobe.service
gives
```
 Loaded: loaded (/etc/init.d/fprobe)
   Active: failed (Result: exit-code) since Wed 2018-11-07 09:09:14 EST; 51s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 2159 ExecStart=/etc/init.d/fprobe start (code=exited, status=1/FAILURE)

Nov 07 09:09:14 filearch.nerc.gov.ua systemd[1]: Starting LSB: NetFlow Collector...
Nov 07 09:09:14 filearch.nerc.gov.ua fprobe[2159]: Starting fprobe: Error in collector #1 parameters
Nov 07 09:09:14 filearch.nerc.gov.ua systemd[1]: fprobe.service: control process exited, code=exited status=1
Nov 07 09:09:14 filearch.nerc.gov.ua systemd[1]: Failed to start LSB: NetFlow Collector.
Nov 07 09:09:14 filearch.nerc.gov.ua systemd[1]: Unit fprobe.service entered failed state.
Nov 07 09:09:14 filearch.nerc.gov.ua systemd[1]: fprobe.service failed.


```
fprobe default configuration file
```
INTERFACE="eth0"
FLOW_COLLECTOR="&#1084;&#1086;&#1081; ip:5115"
#fprobe can't distinguish IP packet from other (e.g. ARP)
OTHER_ARGS="-fip"
```


Please help what to do 

i did ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
``` but nothing changed

what is an error E: Sub-process /usr/bin/dpkg returned an error code (1) ? what i should have to get it right

---

