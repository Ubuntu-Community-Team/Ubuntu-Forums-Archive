---
title: "dante-server install problem"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by halfmike on 2008-07-07
is this a problem with the package or my computer?
also, if anyone could tell me how to set up a socks proxy on port 1080 of my localhost, please do, i think this must be fixed first, though.
```
halfmike@halfmike-laptop:~$ sudo apt-get install dante-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  dante-server
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/132kB of archives.
After this operation, 8192B of additional disk space will be used.
(Reading database ... 203029 files and directories currently installed.)
Preparing to replace dante-server 1.1.18-2.1 (using .../dante-server_1.1.18.dfsg-0.1_amd64.deb) ...
Unpacking replacement dante-server ...
Setting up dante-server (1.1.18.dfsg-0.1) ...
Starting Dante SOCKS daemon: Jul  7 12:39:06 (1215448746) danted[0]: socks_seteuid(): old: 0, new: 13
Jul  7 12:39:06 (1215448746) danted[0]: socks_reseteuid(): current: 13, new: 0
Jul  7 12:39:06 (1215448746) danted[0]: socks_seteuid(): old: 0, new: 65534
Jul  7 12:39:06 (1215448746) danted[0]: socks_reseteuid(): current: 65534, new: 0
Jul  7 12:39:06 (1215448746) danted[0]: socks_seteuid(): old: 0, new: 65534
Jul  7 12:39:06 (1215448746) danted[0]: socks_reseteuid(): current: 65534, new: 0
Jul  7 12:39:06 (1215448746) danted[0]: fixsettings(): no internal address given
Jul  7 12:39:06 (1215448746) danted[0]: sockdexit(): terminating
invoke-rc.d: initscript danted, action "start" failed.
dpkg: error processing dante-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dante-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
halfmike@halfmike-laptop:~$ sudo apt-get install dante-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dante-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up dante-server (1.1.18.dfsg-0.1) ...
Starting Dante SOCKS daemon: Jul  7 12:39:41 (1215448781) danted[0]: socks_seteuid(): old: 0, new: 13
Jul  7 12:39:41 (1215448781) danted[0]: socks_reseteuid(): current: 13, new: 0
Jul  7 12:39:41 (1215448781) danted[0]: socks_seteuid(): old: 0, new: 65534
Jul  7 12:39:41 (1215448781) danted[0]: socks_reseteuid(): current: 65534, new: 0
Jul  7 12:39:41 (1215448781) danted[0]: socks_seteuid(): old: 0, new: 65534
Jul  7 12:39:41 (1215448781) danted[0]: socks_reseteuid(): current: 65534, new: 0
Jul  7 12:39:41 (1215448781) danted[0]: fixsettings(): no internal address given
Jul  7 12:39:41 (1215448781) danted[0]: sockdexit(): terminating
invoke-rc.d: initscript danted, action "start" failed.
dpkg: error processing dante-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dante-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
halfmike@halfmike-laptop:~$ 

```

---

### Post by kbutcher5 on 2009-02-02
> **halfmike said:**
> 
Jul  7 12:39:06 (1215448746) danted[0]: fixsettings(): no internal address given

There is your problem m8, you just have to set an internal address!
You can find it in the documentation, in you conf file, but to make it easy i'll just explain it:

Use your favorite editor to open you /etc/danted.conf
Inthere you type:
```

internal: $interface/$ipaddress port = $portnumber

$interface/$ipaddress = Type your active network card's name (like eth0), or type the active network card's ip address (like 192.168.1.100).

$portnumber = Is the portnumber you want the proxy to run on.

```

While you are at it, make sure you have an external interface set aswell, to do that, you type this in you .conf file:
```

external: $interface/$ipaddress

```
I hope you can read my rather cryptic way of defining interfaces address and ports ;)

---

