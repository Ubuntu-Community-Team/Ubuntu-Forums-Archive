---
title: "bootchart not working in Ubuntu lucid"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by blade4 on 2011-09-06
Hi everyone . Here's my latest problem with lucid - bootchart simply refuses to work . I've tried reinstalling it several times from synaptic - both bootchart and pybootchartgui . Bootchart simply stops at boot . 

Here's bootchart's output in terminal 

No path given, trying /var/log/bootchart.tgz
warning: path '/var/log/bootchart.tgz' does not exist, ignoring.
Parse error: empty state: '/var/log/bootchart.tgz' does not contain a valid bootchart


And here's a pasteout of my boot.log 


init: bootchart pre-stop process (390) terminated with status 1

fsck from util-linux-ng 2.17.2
init: bootchart post-stop process (391) terminated with status 2

/dev/loop0: clean, 164548/752192 files, 1451527/3006464 blocks (check in 5 mounts)
 * Starting AppArmor profiles       [160G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

[154G[ OK ]
 * Setting sensors limits       [160G 
[154G[ OK ]
 * Loading crashkernel...       [160G 


I thought this could be because I had shifted my var/log to ram so I edited my fstab like so : 

tmpfs /tmp     tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/log tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/log/bootchart tmpfs nodev,nosuid 0 0


And it still refuses to boot . I don't want to remove these entries cuz then my laptop becomes really slow . Is there any other alternative ? Please help me out guys . Thanks in advance .

---

### Post by blade4 on 2011-09-06
Anyone ?

---

