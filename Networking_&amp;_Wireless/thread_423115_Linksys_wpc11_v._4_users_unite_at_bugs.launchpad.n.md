---
title: "Linksys wpc11 v. 4 users unite at bugs.launchpad.net"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by fwheeler_1 on 2007-04-25
Hi fellow Linksys wpc11 v. 4 users-

There seems to be a lot of problems with this card in Feisty 7.04 (here's my thread on the forum: [http://ubuntuforums.org/showthread.php?t=414594&highlight=linksys+wpc11](http://ubuntuforums.org/showthread.php?t=414594&highlight=linksys+wpc11) ).  With Dapper 6.06 and Edgy 6.10, this card worked "out-of-the-box", and it is supposed to with Feisty, too.  Since it is not working correctly in Feisty, it is a bug and I reported it on bugs.launchpad.net ([https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/108687](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/108687) ).  Since there are over 100,000 bugs reported, I wanted to suggest that we all work together to get this fixed, instead of using workarounds, like ndiswrapper and wicd.

One place that could definitely use help is in the info needed by the developers to solve the problem .  Unfortunately, I uninstalled Feisty when I couldn't get it work with wireless networking and went back to Edgy before I found that this information was needed.  If someone with Feisty still installed (but before ndiswrapper,  wicd, or some other fix is used) can post this info to lauchpad, it would really assist our efforts in getting this working the way we would all like it to.

The info needed (but never supplied to developers) is given in another bug report filed for the wpc11 ([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/99651](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/99651) ):

[I]Thanks for taking the time to report this bug and helping to make Ubuntu better. Unfortunately we can't fix it, because your description doesn't yet have enough information.
Please include the following additional information, if you have not already done so (please pay attention to lspci's additional options), as required by the Ubuntu Kernel Team:
1. Please include the output of the command 'uname -a' in your next response. It should be one, long line of text which includes the exact kernel version you're running, as well as the CPU architecture.
2. Please run the command 'dmesg > dmesg.log' and attach the resulting file 'dmesg.log' to this bug report.
3. Please run the command 'sudo lspci -vvnn > lspci-vvnn.log' and attach the resulting file 'lspci-vvnn.log' to this bug report.
For your reference, the full description of procedures for kernel-related bug reports is available at [https://wiki.ubuntu.com/KernelTeamBugPolicies](https://wiki.ubuntu.com/KernelTeamBugPolicies) . Thanks in advance![/I]

Another area to help is go to one of the reported bugs and document that you, too, have this problem.  I don't think the developers have the time to search forums to see how prevalent a bug is--so let's help them understand that it is a big issue that needs to be resolved soon!  Thanks for your help.

--Fw

---

### Post by kweejibo on 2007-04-25
Hi FW,

still wrestling with Feisty and my WPC11 v4 card. I haven't gone so far as to do a clean install yet, so I coded:```
ndiswrapper -r NET8180
``` to get rid of the windows driver and disable the card. Then I ran dmesg and lspci-vvnn and posted the log files. Hope they help.

Josh

---

### Post by fwheeler_1 on 2007-04-25
Thanks, Josh.  There are so many bugs posted on launchpad that any help we can give the developers to fix this problem has got to be a good thing.  --Fw

---

### Post by fwheeler_1 on 2007-04-26
Hi Josh-  Thanks again for posting the info.  Because I think the older bug report by another person has been shelved, I moved your info (with reference) to my bug report.

Again, the more linksys wpc11 v. 4 users that go to the official Ubuntu site ( [https://bugs.launchpad.net/](https://bugs.launchpad.net/) ) to support this bug report, the more likely it will get fixed.  This card worked "out-of-the-box" with 6.06 and 6.10, and it should with Feisty, too.  --Fw


> **kweejibo said:**
> Hi FW,

still wrestling with Feisty and my WPC11 v4 card. I haven't gone so far as to do a clean install yet, so I coded:```
ndiswrapper -r NET8180
``` to get rid of the windows driver and disable the card. Then I ran dmesg and lspci-vvnn and posted the log files. Hope they help.

Josh

---

