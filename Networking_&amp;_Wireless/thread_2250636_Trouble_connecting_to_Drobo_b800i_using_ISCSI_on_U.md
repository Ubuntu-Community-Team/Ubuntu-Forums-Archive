---
title: "Trouble connecting to Drobo b800i using ISCSI on Ubuntu 14.04"
date: 2014-10-29
forum: Networking &amp; Wireless
---

### Post by AB81 on 2014-10-29
I have a new Drobo b800i that I am having trouble connecting to an Ubuntu 14.04 workstation. Any help is appreciated. This is a completely fresh installation, so all the settings I haven't changed are the default. My main source of info is the guide on [http://drobo-utils.sourceforge.net/](http://drobo-utils.sourceforge.net/) , but that doesn't seem to be working out. I'll walk you through what I've done and maybe someone can point out something wrong: 

1) I connected the drobo to a Mac with the USB and created the volume. I have tried with and without CHAP authentication turned on, and neither seems to change anything. I can connect to the Mac using the ethernet cable and it recognizes it fine, so I don't think its a setting on the Drobo. 

2) Using the default networking info from the drobo (IP address: 169.254.2.0, netmask: 255.255.0.0, gateway: 169.254.0.1) I set up a new network connection using the "Edit Connections ..." menu. I created a connection on eth0 using manual IPv4 settings. I did not change anything else. At this point I can ping the Drobo and receive this response:

**root@josedell-Precision-T7610:/etc/iscsi# ping 169.254.2.0PING 169.254.2.0 (169.254.2.0) 56(84) bytes of data.**
**64 bytes from 169.254.2.0: icmp_seq=1 ttl=64 time=0.029 ms**
**64 bytes from 169.254.2.0: icmp_seq=2 ttl=64 time=0.029 ms**
**64 bytes from 169.254.2.0: icmp_seq=3 ttl=64 time=0.033 ms**
**64 bytes from 169.254.2.0: icmp_seq=4 ttl=64 time=0.030 ms**
**64 bytes from 169.254.2.0: icmp_seq=5 ttl=64 time=0.031 ms**
**64 bytes from 169.254.2.0: icmp_seq=6 ttl=64 time=0.029 ms**
**^C**
**--- 169.254.2.0 ping statistics ---**
**6 packets transmitted, 6 received, 0% packet loss, time 4999ms**
[B]rtt min/avg/max/mdev = 0.029/0.030/0.033/0.003 ms
[/B]
I assume this means the network connection is working ok? 

2) I've installed open-iscsi and drobo-utils using apt-get. In /etc/iscsi/iscsid.conf , I've tried using CHAP when the the Drobo had CHAP enabled, and not using CHAP when the Drobo had it disabled. When I try iscsiadm using discovery, I get this error message: 

[B][FONT=arial]root@josedell-Precision-T7610:[/FONT][FONT=arial]/etc/iscsi# sudo iscsiadm -m discovery -t sendtargets -p 169.254.2.0[/FONT]
[FONT=arial]iscsiadm: Connection to Discovery Address 169.254.2.0 failed[/FONT]
[FONT=arial]iscsiadm: Login I/O error, failed to receive a PDU[/FONT]
[FONT=arial]iscsiadm: retrying discovery login to 169.254.2.0[/FONT]
[FONT=arial]iscsiadm: Connection to Discovery Address 169.254.2.0 failed[/FONT]
[FONT=arial]iscsiadm: Login I/O error, failed to receive a PDU[/FONT]
[FONT=arial]iscsiadm: retrying discovery login to 169.254.2.0[/FONT]
[FONT=arial]iscsiadm: Connection to Discovery Address 169.254.2.0 failed[/FONT]
[FONT=arial]iscsiadm: Login I/O error, failed to receive a PDU[/FONT]
[FONT=arial]iscsiadm: retrying discovery login to 169.254.2.0[/FONT]
[FONT=arial]iscsiadm: Connection to Discovery Address 169.254.2.0 failed[/FONT]
[FONT=arial]iscsiadm: Login I/O error, failed to receive a PDU[/FONT]
[FONT=arial]iscsiadm: retrying discovery login to 169.254.2.0[/FONT]
[FONT=arial]iscsiadm: Connection to Discovery Address 169.254.2.0 failed[/FONT]
[FONT=arial]iscsiadm: Login I/O error, failed to receive a PDU[/FONT]
[FONT=arial]iscsiadm: retrying discovery login to 169.254.2.0[/FONT]
[FONT=arial]iscsiadm: Connection to Discovery Address 169.254.2.0 failed[/FONT]
[FONT=arial]iscsiadm: Login I/O error, failed to receive a PDU[/FONT]
[FONT=arial]iscsiadm: retrying discovery login to 169.254.2.0[/FONT]
[FONT=arial]iscsiadm: connection login retries (reopen_max) 5 exceeded[/FONT]
[FONT=arial]iscsiadm: Could not perform SendTargets discovery: encountered iSCSI login failure[/FONT][/B]

Sometimes it says "closed" instead of "failed", but the rest of the message is the same. I've also tried using debug mode, and this is the output (passwords redacted): 

[B][FONT=arial]root@josedell-Precision-T7610:[/FONT][FONT=arial]/etc/iscsi# sudo iscsiadm -d 8 -m discovery -t sendtargets -p 169.254.2.0[/FONT]
[FONT=arial]iscsiadm: ip 169.254.2.0, port -1, tgpt -1[/FONT]
[FONT=arial]iscsiadm: Max file limits 1024 4096[/FONT]

[FONT=arial]iscsiadm: updating defaults from '/etc/iscsi/iscsid.conf'[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.sendtargets.auth.[/FONT][FONT=arial]authmethod', 'None' => 'CHAP'[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.sendtargets.auth.[/FONT][FONT=arial]username', '' => 'Drobo'[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.sendtargets.auth.[/FONT][FONT=arial]password', '' => '[REDACTED]'[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.sendtargets.auth.[/FONT][FONT=arial]password_length', '0' => '15'[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.sendtargets.iscsi.[/FONT][FONT=arial]MaxRecvDataSegmentLength', '32768' => '32768'[/FONT]
[FONT=arial]iscsiadm: updated 'node.startup', 'manual' => 'automatic'[/FONT]
[FONT=arial]iscsiadm: updated 'node.leading_login', 'No' => 'No'[/FONT]
[FONT=arial]iscsiadm: updated 'node.session.auth.authmethod'[/FONT][FONT=arial], 'None' => 'CHAP'[/FONT]
[FONT=arial]iscsiadm: updated 'node.session.auth.username', '' => 'Drobo'[/FONT]
[FONT=arial]iscsiadm: updated 'node.session.auth.password', '' => '[/FONT][/B]**[FONT=arial][REDACTED][/FONT]**[B][FONT=arial]'[/FONT]
[FONT=arial]iscsiadm: updated 'node.session.auth.password_[/FONT][FONT=arial]length', '0' => '15'[/FONT]
[FONT=arial]iscsiadm: updated 'node.session.timeo.[/FONT][FONT=arial]replacement_timeout', '120' => '120'[/FONT]
[FONT=arial]iscsiadm: updated 'node.conn[0].timeo.login_[/FONT][FONT=arial]timeout', '30' => '15'[/FONT]
[FONT=arial]iscsiadm: updated 'node.conn[0].timeo.logout_[/FONT][FONT=arial]timeout', '15' => '15'[/FONT]
[FONT=arial]iscsiadm: updated 'node.conn[0].timeo.noop_out_[/FONT][FONT=arial]interval', '5' => '5'[/FONT]
[FONT=arial]iscsiadm: updated 'node.conn[0].timeo.noop_out_[/FONT][FONT=arial]timeout', '5' => '5'[/FONT]
[FONT=arial]iscsiadm: updated 'node.session.err_timeo.abort_[/FONT][FONT=arial]timeout', '15' => '15'[/FONT]
[FONT=arial]iscsiadm: updated 'node.session.err_timeo.lu_[/FONT][FONT=arial]reset_timeout', '30' => '30'[/FONT]
[FONT=arial]iscsiadm: updated 'node.session.err_timeo.tgt_[/FONT][FONT=arial]reset_timeout', '30' => '30'[/FONT]
[FONT=arial]iscsiadm: updated 'node.session.initial_login_[/FONT][FONT=arial]retry_max', '4' => '8'[/FONT]
[FONT=arial]iscsiadm: updated 'node.session.cmds_max', '128' => '128'[/FONT]
[FONT=arial]iscsiadm: updated 'node.session.queue_depth', '32' => '32'[/FONT]
[FONT=arial]iscsiadm: updated 'node.session.xmit_thread_[/FONT][FONT=arial]priority', '-20' => '-20'[/FONT]
[FONT=arial]iscsiadm: updated 'node.session.iscsi.[/FONT][FONT=arial]InitialR2T', 'No' => 'No'[/FONT]
[FONT=arial]iscsiadm: updated 'node.session.iscsi.[/FONT][FONT=arial]ImmediateData', 'Yes' => 'Yes'[/FONT]
[FONT=arial]iscsiadm: updated 'node.session.iscsi.[/FONT][FONT=arial]FirstBurstLength', '262144' => '262144'[/FONT]
[FONT=arial]iscsiadm: updated 'node.session.iscsi.[/FONT][FONT=arial]MaxBurstLength', '16776192' => '16776192'[/FONT]
[FONT=arial]iscsiadm: updated 'node.conn[0].iscsi.[/FONT][FONT=arial]MaxRecvDataSegmentLength', '262144' => '262144'[/FONT]
[FONT=arial]iscsiadm: updated 'node.conn[0].iscsi.[/FONT][FONT=arial]MaxXmitDataSegmentLength', '0' => '0'[/FONT]
[FONT=arial]iscsiadm: updated 'node.session.nr_sessions', '1' => '1'[/FONT]
[FONT=arial]iscsiadm: updated 'node.session.iscsi.FastAbort'[/FONT][FONT=arial], 'Yes' => 'Yes'[/FONT]
[FONT=arial]iscsiadm: Looking for config file /etc/iscsi/send_targets/[/FONT][169.254.2.0]("http://169.254.2.0/")[FONT=arial],3260[/FONT]

[FONT=arial]iscsiadm: Looking for config file /etc/iscsi/send_targets/[/FONT][169.254.2.0]("http://169.254.2.0/")[FONT=arial],3260 config st_config.[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.startup', 'manual' => 'manual'[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.type', 'sendtargets' => 'sendtargets'[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.sendtargets.[/FONT][FONT=arial]address', '' => '169.254.2.0'[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.sendtargets.port', '0' => '3260'[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.sendtargets.auth.[/FONT][FONT=arial]authmethod', 'None' => 'CHAP'[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.sendtargets.auth.[/FONT][FONT=arial]username', '' => 'Drobo'[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.sendtargets.auth.[/FONT][FONT=arial]password', '' => '[/FONT][/B]**[FONT=arial][REDACTED][/FONT]**[B][FONT=arial]'[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.sendtargets.auth.[/FONT][FONT=arial]password_length', '0' => '15'[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.sendtargets.timeo.[/FONT][FONT=arial]login_timeout', '15' => '15'[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.sendtargets.use_[/FONT][FONT=arial]discoveryd', 'No' => 'No'[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.sendtargets.[/FONT][FONT=arial]discoveryd_poll_inval', '30' => '30'[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.sendtargets.reopen_[/FONT][FONT=arial]max', '5' => '5'[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.sendtargets.timeo.[/FONT][FONT=arial]auth_timeout', '45' => '45'[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.sendtargets.timeo.[/FONT][FONT=arial]active_timeout', '30' => '30'[/FONT]
[FONT=arial]iscsiadm: updated 'discovery.sendtargets.iscsi.[/FONT][FONT=arial]MaxRecvDataSegmentLength', '32768' => '32768'[/FONT]
[FONT=arial]iscsiadm: disc rec already exists[/FONT]
[FONT=arial]iscsiadm: Looking for config file /etc/iscsi/send_targets/[/FONT][169.254.2.0]("http://169.254.2.0/")[FONT=arial],3260[/FONT]
[FONT=arial]iscsiadm: starting sendtargets discovery, address [/FONT][169.254.2.0:3260]("http://169.254.2.0:3260/")[FONT=arial], [/FONT]
[FONT=arial]iscsiadm: in read_transports[/FONT]
[FONT=arial]iscsiadm: Adding new transport iser[/FONT]
[FONT=arial]iscsiadm: Matched transport iser[/FONT]
[FONT=arial]iscsiadm: sysfs_attr_get_value: open '/class/iscsi_transport/iser'/[/FONT][FONT=arial]'handle'[/FONT]
[FONT=arial]iscsiadm: sysfs_attr_get_value: new uncached attribute '/sys/class/iscsi_transport/[/FONT][FONT=arial]iser/handle'[/FONT]
[FONT=arial]iscsiadm: sysfs_attr_get_value: add to cache '/sys/class/iscsi_transport/[/FONT][FONT=arial]iser/handle'[/FONT]
[FONT=arial]iscsiadm: sysfs_attr_get_value: cache '/sys/class/iscsi_transport/[/FONT][FONT=arial]iser/handle' with attribute value '18446744072102817824'[/FONT]
[FONT=arial]iscsiadm: sysfs_attr_get_value: open '/class/iscsi_transport/iser'/[/FONT][FONT=arial]'caps'[/FONT]
[FONT=arial]iscsiadm: sysfs_attr_get_value: new uncached attribute '/sys/class/iscsi_transport/[/FONT][FONT=arial]iser/caps'[/FONT]
[FONT=arial]iscsiadm: sysfs_attr_get_value: add to cache '/sys/class/iscsi_transport/[/FONT][FONT=arial]iser/caps'[/FONT]
[FONT=arial]iscsiadm: sysfs_attr_get_value: cache '/sys/class/iscsi_transport/[/FONT][FONT=arial]iser/caps' with attribute value '0x89'[/FONT]
[FONT=arial]iscsiadm: Adding new transport tcp[/FONT]
[FONT=arial]iscsiadm: Matched transport tcp[/FONT]
[FONT=arial]iscsiadm: sysfs_attr_get_value: open '/class/iscsi_transport/tcp'/'[/FONT][FONT=arial]handle'[/FONT]
[FONT=arial]iscsiadm: sysfs_attr_get_value: new uncached attribute '/sys/class/iscsi_transport/[/FONT][FONT=arial]tcp/handle'[/FONT]
[FONT=arial]iscsiadm: sysfs_attr_get_value: add to cache '/sys/class/iscsi_transport/[/FONT][FONT=arial]tcp/handle'[/FONT]
[FONT=arial]iscsiadm: sysfs_attr_get_value: cache '/sys/class/iscsi_transport/[/FONT][FONT=arial]tcp/handle' with attribute value '18446744072101642272'[/FONT]
[FONT=arial]iscsiadm: sysfs_attr_get_value: open '/class/iscsi_transport/tcp'/'[/FONT][FONT=arial]caps'[/FONT]
[FONT=arial]iscsiadm: sysfs_attr_get_value: new uncached attribute '/sys/class/iscsi_transport/[/FONT][FONT=arial]tcp/caps'[/FONT]
[FONT=arial]iscsiadm: sysfs_attr_get_value: add to cache '/sys/class/iscsi_transport/[/FONT][FONT=arial]tcp/caps'[/FONT]
[FONT=arial]iscsiadm: sysfs_attr_get_value: cache '/sys/class/iscsi_transport/[/FONT][FONT=arial]tcp/caps' with attribute value '0x39'[/FONT]

[FONT=arial]iscsiadm: authentication setup complete...[/FONT]
[FONT=arial]iscsiadm: sendtargets discovery to [/FONT][169.254.2.0:3260]("http://169.254.2.0:3260/")[FONT=arial] using isid 0x00023d000000[/FONT]
[FONT=arial]iscsiadm: resolved 169.254.2.0 to 169.254.2.0[/FONT]
[FONT=arial]iscsiadm: discovery timeouts: login 15, reopen_cnt 6, auth 45.[/FONT]
[FONT=arial]iscsiadm: connecting to [/FONT][169.254.2.0:3260]("http://169.254.2.0:3260/")
[FONT=arial]iscsiadm: connected local port 55346 to [/FONT][169.254.2.0:3260]("http://169.254.2.0:3260/")
[FONT=arial]iscsiadm: connected to discovery address 169.254.2.0[/FONT]
[FONT=arial]iscsiadm: discovery session to [/FONT][169.254.2.0:3260]("http://169.254.2.0:3260/")[FONT=arial] starting iSCSI login[/FONT]
[FONT=arial]iscsiadm: sending login PDU with current stage 0, next stage 1, transit 0x80, isid 0x00023d000000 exp_statsn 0[/FONT]
[FONT=arial]iscsiadm: > InitiatorName=iqn.1993-08.org.[/FONT][FONT=arial]debian:01:4cd1b473c8a5[/FONT]
[FONT=arial]iscsiadm: > InitiatorAlias=josedell-[/FONT][FONT=arial]Precision-T7610[/FONT]
[FONT=arial]iscsiadm: > SessionType=Discovery[/FONT]
[FONT=arial]iscsiadm: > AuthMethod=CHAP,None[/FONT]
[FONT=arial]iscsiadm: wrote 48 bytes of PDU header[/FONT][/B]

3) One other worrying issue is that when I connect the Drobo to the Ubuntu machine via USB, I don't see any indication that it is connected, and drobom can't find it. 
4) I've tried adding permissions to iptables and manually configuring the iface, but these were desperation moves and didn't seem to change anything.

Sorry for the long post but I wanted to include as much info as I could. Any help would be appreciated!

---

