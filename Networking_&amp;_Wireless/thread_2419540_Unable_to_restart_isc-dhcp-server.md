---
title: "Unable to restart isc-dhcp-server"
date: 2019-05-23
forum: Networking &amp; Wireless
---

### Post by jobinjv on 2019-05-23
[SIZE=2][FONT=arial][COLOR=#555555]I am trying to restart my isc-dhcp-server and i get the following error. Please suggest a solution

[/COLOR]```
[COLOR=#555555]pi@JsDHCPPi:~$ sudo service isc-dhcp-server restart[/COLOR]
[COLOR=#555555]Job for isc-dhcp-server.service failed because the control process exited with error code.[/COLOR]
[COLOR=#555555]See "systemctl status isc-dhcp-server.service" and "journalctl -xe" for details.[/COLOR]
```
[COLOR=#555555]
```
pi@JsDHCPPi:~$ systemctl status isc-dhcp-server.service
&#9679; isc-dhcp-server.service - LSB: DHCP server
   Loaded: loaded (/etc/init.d/isc-dhcp-server; enabled; vendor preset: enabled)
   Active: activating (auto-restart) (Result: exit-code) since Thu 2019-05-23 23:14:17 +03; 2s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 1318 ExecStart=/etc/init.d/isc-dhcp-server start (code=exited, status=1/FAILURE)

May 23 23:14:17 JsDHCPPi systemd[1]: isc-dhcp-server.service: Control process exited, code=exited status=1
May 23 23:14:17 JsDHCPPi systemd[1]: Failed to start LSB: DHCP server.
May 23 23:14:17 JsDHCPPi systemd[1]: isc-dhcp-server.service: Unit entered failed state.
May 23 23:14:17 JsDHCPPi systemd[1]: isc-dhcp-server.service: Failed with result 'exit-code'.
```[/COLOR]
[COLOR=#555555]
[/COLOR]```
[COLOR=#555555]
pi@JsDHCPPi:~$ journalctl -xe
May 23 23:14:17 JsDHCPPi dhcpd[1329]: 
May 23 23:14:17 JsDHCPPi dhcpd[1329]: exiting.
May 23 23:14:22 JsDHCPPi systemd[1]: isc-dhcp-server.service: Service hold-off time over, scheduling restart.
May 23 23:14:22 JsDHCPPi systemd[1]: Stopped LSB: DHCP server.
-- Subject: Unit isc-dhcp-server.service has finished shutting down
-- Defined-By: systemd
-- Support: [https://www.debian.org/support](https://www.debian.org/support)
-- 
-- Unit isc-dhcp-server.service has finished shutting down.
May 23 23:14:22 JsDHCPPi systemd[1]: Starting LSB: DHCP server...
-- Subject: Unit isc-dhcp-server.service has begun start-up
-- Defined-By: systemd
-- Support: [https://www.debian.org/support](https://www.debian.org/support)
-- 
-- Unit isc-dhcp-server.service has begun starting up.
May 23 23:14:22 JsDHCPPi isc-dhcp-server[1333]: Launching IPv4 server only.
May 23 23:14:22 JsDHCPPi dhcpd[1343]: /etc/dhcp/dhcpd.conf line 0: expecting a parameter or declaration
May 23 23:14:22 JsDHCPPi dhcpd[1343]: 
May 23 23:14:22 JsDHCPPi dhcpd[1343]: ^
May 23 23:14:22 JsDHCPPi dhcpd[1343]: Configuration file errors encountered -- exiting
May 23 23:14:22 JsDHCPPi dhcpd[1343]: 
May 23 23:14:22 JsDHCPPi dhcpd[1343]: If you think you have received this message due to a bug rather
May 23 23:14:22 JsDHCPPi dhcpd[1343]: than a configuration issue please read the section on submitting
May 23 23:14:22 JsDHCPPi dhcpd[1343]: bugs on either our web page at [www.isc.org]("http://www.isc.org") or in the README file
May 23 23:14:22 JsDHCPPi isc-dhcp-server[1333]: dhcpd self-test failed. Please fix /etc/dhcp/dhcpd.conf.
May 23 23:14:22 JsDHCPPi isc-dhcp-server[1333]: The error was:
May 23 23:14:22 JsDHCPPi dhcpd[1343]: before submitting a bug.  These pages explain the proper
May 23 23:14:22 JsDHCPPi dhcpd[1343]: process and the information we find helpful for debugging..
May 23 23:14:22 JsDHCPPi dhcpd[1343]: 
May 23 23:14:22 JsDHCPPi dhcpd[1343]: exiting.
May 23 23:14:22 JsDHCPPi dhcpd[1344]: Internet Systems Consortium DHCP Server 4.3.5
May 23 23:14:22 JsDHCPPi isc-dhcp-server[1333]: Internet Systems Consortium DHCP Server 4.3.5
May 23 23:14:22 JsDHCPPi isc-dhcp-server[1333]: Copyright 2004-2016 Internet Systems Consortium.
May 23 23:14:22 JsDHCPPi isc-dhcp-server[1333]: All rights reserved.
May 23 23:14:22 JsDHCPPi isc-dhcp-server[1333]: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
May 23 23:14:22 JsDHCPPi dhcpd[1344]: Copyright 2004-2016 Internet Systems Consortium.
May 23 23:14:22 JsDHCPPi isc-dhcp-server[1333]: /etc/dhcp/dhcpd.conf line 0: expecting a parameter or declaration
May 23 23:14:22 JsDHCPPi isc-dhcp-server[1333]: ^
May 23 23:14:22 JsDHCPPi dhcpd[1344]: All rights reserved.
May 23 23:14:22 JsDHCPPi isc-dhcp-server[1333]: Configuration file errors encountered -- exiting
May 23 23:14:22 JsDHCPPi isc-dhcp-server[1333]: If you think you have received this message due to a bug rather
May 23 23:14:22 JsDHCPPi isc-dhcp-server[1333]: than a configuration issue please read the section on submitting
May 23 23:14:22 JsDHCPPi isc-dhcp-server[1333]: bugs on either our web page at [www.isc.org]("http://www.isc.org") or in the README file
May 23 23:14:22 JsDHCPPi isc-dhcp-server[1333]: before submitting a bug.  These pages explain the proper
May 23 23:14:22 JsDHCPPi isc-dhcp-server[1333]: process and the information we find helpful for debugging..
May 23 23:14:22 JsDHCPPi isc-dhcp-server[1333]: exiting.
May 23 23:14:22 JsDHCPPi dhcpd[1344]: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
May 23 23:14:22 JsDHCPPi systemd[1]: isc-dhcp-server.service: Control process exited, code=exited status=1
May 23 23:14:22 JsDHCPPi dhcpd[1344]: /etc/dhcp/dhcpd.conf line 0: expecting a parameter or declaration
May 23 23:14:22 JsDHCPPi systemd[1]: Failed to start LSB: DHCP server.
-- Subject: Unit isc-dhcp-server.service has failed
-- Defined-By: systemd
-- Support: [https://www.debian.org/support](https://www.debian.org/support)
-- 
-- Unit isc-dhcp-server.service has failed.
-- 
-- The result is failed.
May 23 23:14:22 JsDHCPPi dhcpd[1344]: 
May 23 23:14:22 JsDHCPPi systemd[1]: isc-dhcp-server.service: Unit entered failed state.
May 23 23:14:22 JsDHCPPi dhcpd[1344]: ^
May 23 23:14:22 JsDHCPPi systemd[1]: isc-dhcp-server.service: Failed with result 'exit-code'.
May 23 23:14:22 JsDHCPPi dhcpd[1344]: Configuration file errors encountered -- exiting
May 23 23:14:22 JsDHCPPi dhcpd[1344]: 
May 23 23:14:22 JsDHCPPi dhcpd[1344]: If you think you have received this message due to a bug rather
May 23 23:14:22 JsDHCPPi dhcpd[1344]: than a configuration issue please read the section on submitting
May 23 23:14:22 JsDHCPPi dhcpd[1344]: bugs on either our web page at [www.isc.org]("http://www.isc.org") or in the README file
May 23 23:14:22 JsDHCPPi dhcpd[1344]: before submitting a bug.  These pages explain the proper
May 23 23:14:22 JsDHCPPi dhcpd[1344]: process and the information we find helpful for debugging..
May 23 23:14:22 JsDHCPPi dhcpd[1344]: 
May 23 23:14:22 JsDHCPPi dhcpd[1344]: exiting.[/COLOR]
```[/FONT][/SIZE]

---

### Post by ogeron on 2019-05-23
What's this file look like? 

[COLOR=#555555]May 23 23:14:22 JsDHCPPi dhcpd[1343]: /etc/dhcp/dhcpd.conf line 0: expecting a parameter or declaration[/COLOR]

---

### Post by jobinjv on 2019-05-23
The issue was found as a time stamp that popped by at the beginning of the dhcpd.conf file

---

