---
title: "systemd reports &quot;Failed to start Login to default iSCSI targets.&quot;"
date: 2021-06-05
forum: Networking &amp; Wireless
---

### Post by fredsmith2021 on 2021-06-05
Hi,

I am using an Ubuntu 20.04 64-bit box as an iSCSI initiator to connect to a Synology NAS.  The first point to make is that the iSCSI drives are both mapped and accessible.  After issues with the Synology NAS which required me to reinstall the operating system, I had to reconnect the initiator to the targets.  Hitherto there were no issues with connecting to the targets of which I am aware.

Prior to the systemd report stated in the Title there is a sequences of 81 log entries from iscsid "cannot make a connection to fe80::211:32ff:fea5:ef01:3260 (-1,22)".  It appears to me that this issue relates to IPv6.  My network uses IPv4 and I have IPv6 switched off on both the Synology and on the Ubuntu box.

Any ideas on how and where to disable the attempt to connect on IPv6 would be gratefully considered.

Thanks

Okay, first and final edit.  

When I ran:

  	 	 	 	  [LEFT] sudo iscsiadm -m node -P 1[/LEFT]  

I got:

   	 	 	 	  [LEFT] Target: iqn.2000-01.com.synology:SynDS418.Target-1.e3dc536b29[/LEFT] [LEFT] 	
Portal: 192.168.100.146:3260,1
[/LEFT] [LEFT] 		Iface Name: default

[/LEFT] [LEFT] 	Portal: [fe80::211:32ff:fea5:ef01]:3260,1
[/LEFT] [LEFT] 		Iface Name: default
[/LEFT] [LEFT] 
Target: iqn.2019-10-20.com.synology:SynDS418.Target-1.e3dc536b29
[/LEFT] [LEFT] 	
Portal: 192.168.100.146:3260,1
[/LEFT] [LEFT] 		Iface Name: default
[/LEFT] [LEFT] 	
Portal: [fe80::211:32ff:fea5:ef01]:3260,1
Iface Name: default
[/LEFT]  
I entered the command:

  	 	 	 	  [LEFT] sudo iscsiadm -m node -o delete -T iqn.2019-10-20.com.synology:SynDS418.Target-1.e3dc536b29 -p [fe80::211:32ff:fea5:ef01]:3260

And after the offending Portal was gone.  I repeated for the remaining IQN and both entries were removed.  After, upon reboot, no more adverse entries in the log file.
[/LEFT]

---

