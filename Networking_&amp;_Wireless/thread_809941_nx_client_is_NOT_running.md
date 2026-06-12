---
title: "nx client is NOT running"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by lovelain on 2008-05-27
1. NX client connection error
I got remote control progaram NX from nomachine. I installed nxserver to Ubuntu 7.10. and connect with nx client. 
There is following message.

```

Info: Display running with pid '0' and handler '0x54'.

NXPROXY - Version 3.2.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '5828'.
Session: Starting session at 'Mon May 26 11:14:32 2008'.
Error: Can't determine the location of the X display socket.
Error: Error 2 'No such file or directory' checking '&#21983;????&#45917;wE?w????/.X11-unix'.
Session: Session terminated at 'Mon May 26 11:14:32 2008'.

```

server: ubuntu 7.10 nxserver_3.2.0-7
client: Windows Vista nxclient-3.2.0-10

 
Until connection is established, operation is fine. but not work for opening session.
maybe I think .X11-unix permission problem. 
then I modify permission, still problem is same.

This is /var/log/messages
```

May 28 09:35:53 lovelain NXSERVER-3.2.0-7[15902]: User 'timberwolf' logged in from '192.168.0.1'. 'NXLogin::set'
May 28 09:35:53 lovelain NXSERVER-3.2.0-7[15902]: Selected node host:localhost with port:22 'main::selectNode'
May 28 09:35:53 lovelain NXSERVER-3.2.0-7[15902]: Current selected node: localhost is in status: running  'main::selectNode'
May 28 09:35:54 lovelain NXSERVER-3.2.0-7[15902]: Selected session type: unix-console allowed in the profile of user: timberwolf 'NXShell::Static'
May 28 09:35:59 lovelain NXSERVER-3.2.0-7[15902]: Session '6B9E1D25501D080C9D8EAC9B959E5451' started by user 'timberwolf'. 'NXShell::handler_session_start'
May 28 09:35:59 lovelain NXSERVER-3.2.0-7[15902]: User 'timberwolf' from '192.168.0.1' logged out. 'NXLogin::reset'
May 28 09:35:59 lovelain NXNODE-3.2.0-5[15918]: Using port '1001' on node 'lovelain' for session 'unix-console'. Logger::log nxnode 5975
May 28 09:35:59 lovelain NXNODE-3.2.0-5[15918]: Using host from available host list: '192.168.0.7'. Logger::log nxnode 5976
May 28 09:36:03 lovelain NXNODE-3.2.0-5[15918]: ERROR: run command: process: 15942 finished with: 1 Logger::log nxnode 3764
May 28 09:36:03 lovelain NXNODE-3.2.0-5[15947]: ERROR: Error when monitoring session: Unable to open display 'nx/nx,options=/home/timberwolf/.nx/C-lovelain-1001-6B9E1D25501D080C9D8EAC9B959E5451/options:1001' 'NXSessionMonitor::__setSessionStatus'
May 28 09:36:04 lovelain NXNODE-3.2.0-5[15947]: Directory '/home/timberwolf/.nx/C-lovelain-1001-6B9E1D25501D080C9D8EAC9B959E5451' renamed into '/home/timberwolf/.nx/F-C-lovelain-1001-6B9E1D25501D080C9D8EAC9B959E5451' for further investigation Logger::log nxnode 6155
May 28 09:36:05 lovelain NXNODE-3.2.0-5[15918]: Session 'unix-console' on port '1001' failed. Logger::log nxnode 6234
May 28 09:36:11 lovelain NXSERVER-3.2.0-7[15943]: ERROR: NXNodeExec: Cannot kill nxssh process: No such process 'NXNodeExec::exec'
May 28 09:36:11 lovelain NXSERVER-3.2.0-7[15943]: User 'timberwolf' from '192.168.0.1' logged out. 'NXLogin::reset'

```

p.s. when I connect nxserver with Ubuntu nxclient, connection is normally.

2. nxmanager is NOT working

browsing [http://localhost/nxmanager/](http://localhost/nxmanager/)
error message is following:

```

You don't have permission to access /nxmanager/ on this server.

```

---

