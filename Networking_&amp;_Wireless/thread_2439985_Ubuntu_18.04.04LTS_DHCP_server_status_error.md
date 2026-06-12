---
title: "Ubuntu 18.04.04LTS DHCP server status error"
date: 2020-04-04
forum: Networking &amp; Wireless
---

### Post by itsshowtime on 2020-04-04
Hi community,

I am experiencing a status error for my **isc-dhcp-server on Ubuntu Bionic Beaver**. I think it might have to do with the wireless configuration I added in the dhcpd.conf file, although this is coming from the Cisco official webpage you can find here: [https://www.cisco.com/c/en/us/support/docs/wireless-mobility/wireless-lan-wlan/97066-dhcp-option-43-00.html#toc-hId-1101475086](https://www.cisco.com/c/en/us/support/docs/wireless-mobility/wireless-lan-wlan/97066-dhcp-option-43-00.html#toc-hId-1101475086)

It looks fairly straight forward and I cannot find syntax issues in the file (keep in mind I am a complete noob at this), nor can I find out how to actually see where the process gets stuck (which line in the file).

If anyone can help me find out what's the issue or how to troubleshoot this, that would be very much appreciated!

**error output:**
```

sdaadmin@pod1-dhcp:~$ systemctl status isc-dhcp-server
&#9679; isc-dhcp-server.service - ISC DHCP IPv4 server
   Loaded: loaded (/lib/systemd/system/isc-dhcp-server.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2020-04-03 12:37:52 CEST; 5s ago
     Docs: man:dhcpd(8)
  Process: 2552 ExecStart=/bin/sh -ec      CONFIG_FILE=/etc/dhcp/dhcpd.conf;      if [ -f /etc/ltsp/dhcpd.conf ]; then CONFIG_FILE=/etc/ltsp/dhcpd.conf; fi;      [ -e /var/lib/dhcp/dhcpd.leases ] || touch
 Main PID: 2552 (code=exited, status=1/FAILURE)


Apr 03 12:37:52 pod1-dhcp dhcpd[2552]:  ^
Apr 03 12:37:52 pod1-dhcp dhcpd[2552]: Configuration file errors encountered -- exiting
Apr 03 12:37:52 pod1-dhcp dhcpd[2552]: 
Apr 03 12:37:52 pod1-dhcp dhcpd[2552]: If you think you have received this message due to a bug rather
Apr 03 12:37:52 pod1-dhcp dhcpd[2552]: than a configuration issue please read the section on submitting
Apr 03 12:37:52 pod1-dhcp dhcpd[2552]: bugs on either our web page at www.isc.org or in the README file
Apr 03 12:37:52 pod1-dhcp dhcpd[2552]: before submitting a bug.  These pages explain the proper
Apr 03 12:37:52 pod1-dhcp dhcpd[2552]: process and the information we find helpful for debugging..
Apr 03 12:37:52 pod1-dhcp dhcpd[2552]: 
Apr 03 12:37:52 pod1-dhcp dhcpd[2552]: exiting.

```

**I attached /etc/dhcp/dchpd.conf**

---

