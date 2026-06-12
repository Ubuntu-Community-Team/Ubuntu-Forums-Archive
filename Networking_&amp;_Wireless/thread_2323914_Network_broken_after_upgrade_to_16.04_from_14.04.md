---
title: "Network broken after upgrade to 16.04 from 14.04"
date: 2016-05-09
forum: Networking &amp; Wireless
---

### Post by Princey on 2016-05-09
I upgraded my server running in a VM from 14.04 to 16.04 over the weekend and first thing I noticed was I lost remote access. Physically logging into the machine I can't get an IP address so I checked the logs. Here are the screenshots of the logs and commands to try to resolve the issue.

```
systemctl status network.service 
```

[ATTACH=CONFIG]268953[/ATTACH]

The journalcl -xe command gives me the following: [ATTACH=CONFIG]268955[/ATTACH]. If I manually try to bring it up with the sudo if up command, I get this: [ATTACH=CONFIG]268956[/ATTACH]. Any ideas would be appreciated. Thanks.

---

### Post by Princey on 2016-05-09
I solved the problem, finally, but would like to post the solution just in case someone else runs into the same issue. Apparently, running the command ```
ip link 
``` revealed that somehow, the network interface was renamed during the upgrade from eth0 to ens33. I just edited the /etc/network/interfaces line where eth0 is referenced changing it to ens33, restarted the networking system, and voila, network access achieved.

---

### Post by RobGoss on 2016-05-09
Thanks for sharing Your solution with the Forum if you don't mind would you mark this threadm as solved

---

### Post by Princey on 2016-05-09
Done!!

---

