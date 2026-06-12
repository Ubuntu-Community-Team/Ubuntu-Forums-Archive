---
title: "Dual boot with W2k8 on nForce4 Raid 1?"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by Nyodulf on 2011-06-24
Hi all, totally new to all this here. I've been determined to get Ubuntu running on this machine and have had about 2 weeks of pain (not all related to Ubuntu by any stretch).

Anyway, I have an AMD Athlon 64 x2 computer with Windows Server 2008 installed and running fine on a RAID 1 nForce4 array. I would like to set up a dual boot with Ubuntu, and I tried the Wubi install with a local .ISO (ubuntu-11.04-desktop-amd64.iso) with the wubi installer from the correct directory.

When the system reboots after the Windows install process, I chose the verbose option. All the text readout went fine, but when the GUI loaded, after going through an installation verification process, I got the error: "no root file system found".

After some searching, I tried hitting CTRL-ALT-F2 and typing: *sudo sh /host/ubuntu/install/custom-installation/hooks/failure-command.sh*

but I got the error: *sh: Can't open sudo sh /host/ubuntu/install/custom-installation/hooks/failure-command.sh*

I would be grateful for any suggestions. I'm happy to try a less user-friendly method, but I have no experience with any form of Linux, and I suspect that my RAID array is part of the problem.

Cheers!
Nyo

---

### Post by cariboo on 2011-06-25
Yes the raid array is the problem, you can't install ubuntu on a raid array with Windows on it already. If you can add another hard drive, either SATA, PATA or usb, you should be able to install Ubuntu without a problem.

---

### Post by Rubi1200 on 2011-06-25
Another point to consider is that although, theoretically, Wubi can be installed on RAID, in practice we have seen few cases where it is actually successful.

I recommend following cariboo907's advice and install an extra drive where you can put Ubuntu (regular install not Wubi).

Good luck and let us know if you need more help.

---

### Post by Nyodulf on 2011-06-25
Thanks for the response; I already have another disk in the computer, but it's a single disk in a JBOD array - would that work? There's no Windows  installation on it. At the moment it is a large disk divided into 5  partitions. I could shrink one by 30GB to create a partition for  Ubuntu...

---

