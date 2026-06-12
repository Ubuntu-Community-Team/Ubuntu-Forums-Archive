---
title: "Ubuntu 12.04.4 LTS and open-iscsi 2.0.871 eth0/eth1 Problem"
date: 2014-04-11
forum: Networking &amp; Wireless
---

### Post by Larry Mateo on 2014-04-11
I recently built a Ubuntu 12.04.4 LTS server. Before I installed the open-iscsi package (version 2.0.871), I configured two Ethernet interfaces (eth0 and eth1) and tested connectivity with both. All tests passed.

After I installed open-iscsi (apt-get install open-iscsi), when I boot the server, either eth0 or eth1 does not come up. If I manually start networking, both NICs come up fine and work as expected. As a quick fix, I have added the line '/etc/init.d/networking start' to the server's /etc/rc.local file, but I would like to find a more suitable solution , or even find out why open-iscsi is stomping on eth0/eth1 when the server is coming up.

Some other stuff:
-The server is a Dell PowerEdge R610 with four onboard Broadcom NICs.
-For debugging purposes, I disabled the four Broadcom NICS on the motherboard, installed an Intel NIC, and re-installed 12.04.4 LTS. The same problem occurred.
-I have searched the various /var/log/* files, but have found no explanation as to why the problem occurs.
-The following two lines are in the /var/log/boot.log file
* Starting configure network device [fail]
* Stopping configure network device used by iSCSI root [OK]
I'm not sure if the second line points to a conflict or not.
-The problem occurs whether or not I set node.startup to manual or automatic in the /etc/iscsi/iscsid.conf file.
-All open-iscsi settings are set to the defaults.
-I went to the open-iscsi web site ([http://www.open-iscsi.org/](http://www.open-iscsi.org/)) and found that there is a more current version available--2.0.873. But, honestly, the installation procedure is Greek to me.

If you have questions, please ask away.

Thanks much.

---

