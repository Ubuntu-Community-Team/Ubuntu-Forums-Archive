---
title: "Network IP settings needs to be entered each time I login"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by ron_max on 2008-11-18
Installed a fresh copy of Ubuntu 8.10 on Intel i386 32 bit dual core laptop. Ethernet adapter has been detected fine but each time I restart, I need to set up the network ip,dns server,netmask,gateway everything again for using the network. What can I do??  ..help me out please ... Also the system is taking too long time(more than 5 minutes)to shut down. :confused::confused::confused:

---

### Post by Iowan on 2008-11-18
Network Manager had a problem with static (manual) configurations.  I saw a thread suggesting it had been fixed, but I presume it'd require an update (which a fresh install might not have gotten - yet).

In the meantime, [here]("http://ubuntuforums.org/showthread.php?t=974382") is a workaround that might help.

---

### Post by ron_max on 2008-11-19
hey thanks a lot ! It worked for me as well as my friends.. but I have developed a problem that my laptop is not discovering the local network anymore and i cannot access any other computer neither my computer can be accessed. samba is installed.

---

### Post by Iowan on 2008-11-19
You've verified that machines are in same subnet (via **ifconfig** on Ubuntu - **ipconfig/all** on XP (dunno about Vista).  FYI, [here]("http://ubuntuforums.org/showthread.php?t=202605") is a good How-To on peer-to-peer networking with Windows.

---

### Post by ron_max on 2008-11-22
thanks for efforts .. after a restart the problem was solved.. =):popcorn:

---

### Post by Iowan on 2008-11-24
GREAT!! Do me a favor (so I'll quit checking this thread) -  mark it as [SOLVED] (Under Thread Tools).

---

