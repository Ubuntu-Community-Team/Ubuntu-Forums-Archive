---
title: "Network manager error"
date: 2023-06-01
forum: Networking &amp; Wireless
---

### Post by triorez-25b on 2023-06-01
I was trying to fix my Wi-Fi running slow on Ubuntu in comparison to Windows in the process I appear to have broken my network manager it refuses to start giving the error code "exited"
Prompting me to use "systemclt status networkmanager.service" which gave me * NetworkManager.service - Network Manager
Loaded: loaded (/pob/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
Active: failed (Result: exit-codr) since Thu 2023-06-01 00:58:47 EDT; 57s ago
Docs: man:NetworkManager(8)
Process: 3667 ExecStart=/usr/sbin/NetworkManager --no-daemon (code=exited, status=1/FAILURE)
Main PID: 3667 (code=exited, status=1/FAILURE)
CPU: 9ms 
And it prompted me to use "journalctl -xeu NetworkManager.service"
 That resulted in 
Subject: Unit process exited
Defined-By: systemd
Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
An ExecStart= process belonging to unit NetworkManager.service has exited.
The process' exit code is 'exited' and its exit status is 1.
jun 01 00:58:46 triorez-MS-7C80 systemd[1]: NetworkManager.service: Failed with result 'exit-code'.
Subject: Unit failed
Defined-By:systemd
Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
The unit NetworkManager.service has entered the 'failed' state with result 'exit-code'.
jun 01 00:58:46 triorez-MS-7C80 systemd[1]: Failed to start Network Manager.
Subject: A start job for unit NetworkManager.service has failed
Defined-By:systemd
Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
A start job for unit NetworkManager.service has finished with a failure.
The job identifier is 4203 and the job result ts failed.
jun 01 00:58:47 triorez-MS-7C80 systemd[1]: NetworkManager.service:Scheduled restart job,restart counter is at 5.
Subject:Automatic restarting of a unit has been scheduled
Defined-By:systemd
Support:[http://www.ubuntu.com/support](http://www.ubuntu.com/support)
Automatic restarting of the unit NetworkManager.service has been scheduled,as the result for
the configured Restart= setting for the unit.
Jun 01 00:58:47 triorez-MS-7C80 systemd[1]: Stopped Network Manager.
Subject: A stop job for unit NetworkManager.service has finished
Defined-By: systemd
Support: [http://www.ubuntu.con/support](http://www.ubuntu.con/support)
A stop job for unit NetworkManager.service has finished.
The job identifler is 4294 and the job result is done.
jun 01 00:58:47 triorez-MS-7C80 systemd[1]: NetworkManager.service:Start request repeated too quickly.
jun 01 00:58:47 triorez-MS-7C80 systemd[1]: NetworkManager.service: Failed with result 'exit-code'.
Subject:Unit failed
Defined-By: systemd
Support: [http://waw.ubuntu.com/support](http://waw.ubuntu.com/support)
The unit NetworkManager.service has entered the 'failed' state with result 'exit-code''. 
Jun 01 00:58:47 triorez-MS-7C80 systemd[1]:Failed to start Network Manager.
Subject:A start job for unit NetworkManager.service has failed
Defined-By: systemd
Support:[http://www.ubuntu.com/support](http://www.ubuntu.com/support)
A start job for unit NetworkManager.service has finished with a failure,
The job identifier is 4294 and the job result is failed.
Any advice on how to get my wifi back?

---

