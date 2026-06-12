---
title: "Copying file to windows share causes system to freeze"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by BillMahr on 2007-11-01
There does not seem to be any posts with my problem so I'll try to describe it.

I have a local wired network with two windows computers and a third computer running edubuntu 7.10.  When I was using version 7.04 I could copy files between the edubuntu computer and a shared folder on a windows XP system with no problems.  Since I upgraded to 7.10 anytime I try to copy a large file from edubuntu to the windows share the system freezes completely.  No response at all to the mouse or keyboard.  Transfers in the other direction work or at least work more reliably.  The symptom does not appear to be constant.  The time into the transfer when the freeze occurs does not appear to be constant.

The problem seems to be in my computer or a driver.  After booting from a ubuntu 7.10 CD I get the same problem.  However after booting from the same CD on another system I could NOT duplicate the problem.  

I really do not have enough experience with Linux to troubleshoot the problem.  So if anyone has any suggestions on where I should start looking I would appreciate it.

Thanks,

Bill

---

### Post by Lambert on 2007-11-02
> **BillMahr said:**
> There does not seem to be any posts with my problem so I'll try to describe it.

I have a local wired network with two windows computers and a third computer running edubuntu 7.10.  When I was using version 7.04 I could copy files between the edubuntu computer and a shared folder on a windows XP system with no problems.  Since I upgraded to 7.10 anytime I try to copy a large file from edubuntu to the windows share the system freezes completely.  No response at all to the mouse or keyboard.  Transfers in the other direction work or at least work more reliably.  The symptom does not appear to be constant.  The time into the transfer when the freeze occurs does not appear to be constant.

The problem seems to be in my computer or a driver.  After booting from a ubuntu 7.10 CD I get the same problem.  However after booting from the same CD on another system I could NOT duplicate the problem.  

I really do not have enough experience with Linux to troubleshoot the problem.  So if anyone has any suggestions on where I should start looking I would appreciate it.

Thanks,

Bill


Start by going into the administration menu and open up system log. When your system boots it will write a bunch of stuff here, find the time frame when you had the freeze and see if there is any errors or warning listed.

---

### Post by BillMahr on 2007-11-03
Thanks for the suggestion.  No faults right before the freeze up but a couple of warnings at startup.  Could I ask what these messages mean?

Nov  2 15:22:54 dualCPU dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Nov  2 15:22:56 dualCPU kernel: [  194.045874] NET: Registered protocol family 17
Nov  2 15:22:57 dualCPU dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Nov  2 15:22:57 dualCPU dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Nov  2 15:22:57 dualCPU dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers

Bill

---

