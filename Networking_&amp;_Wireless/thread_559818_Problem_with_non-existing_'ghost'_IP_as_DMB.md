---
title: "Problem with non-existing 'ghost' IP as DMB"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by Akula on 2007-09-25
Hello,

Situation: I suddenly noted that my ubuntu 7.04 server just stopped responsing to SSH, NX(remote desktop), and web service calls, but responded to ping. After a while I rebooted server with reset button and after system came to online I could log into it via remote desktop NX (after few attemps).

Browsed syslog for a while and found following:

```

nmbd/nmbd_become_dmb.c:become_domain_master_browser_wins(349)
become_domain_master_browser_wins: querying WINS server from IP 192.168.0.90 for domain master browser name MSHOME<1b> on workgroup MSHOMe
nmbd/nmbd_become_dmb.:become_domain_master_query_success(233)
become_domain_master_query_success:
There is already a domain master browser at IP 192.168.0.102 for workgroup MSHOME registered on submet UNICAST_SUBNET.

nmbd_browsesync.c:domain_master_node_status_fail(258)
domain_master_node_status_fail:
Doing a node status request to the domain master browser
for workgroup MASHOME at 192.168.0.102 failed.
Cannot sync browser lists.

```

I'm not certain if this actually caused the problem (I'm using samba for sharing files on server with winXP computers and sharing works even if such lines keep appearing into syslog).

About these lines I can tell, that IP 192.168.0.102 USED to be ubuntu server's IP UNTIL I changed it to 192.168.0.90 manually (there is no longer computer with IP 192.168.0.102 in my LAN). I also checked /etc/network/interfaces and it was changed to there as well. I wonder where the old address might still be, if syslog keeps producing such lines. Can you help me at all with this?

EDIT:
It also appears that no-longer-shared directories on UBUNTU SERVER can be seen in my WinXP network shares. This is probably cause of the problem described above.

---

### Post by Akula on 2007-09-26
bump

---

### Post by Akula on 2007-09-27
Anyone?

---

