---
title: "Slow down on localhost after canonical live patch update"
date: 2018-10-13
forum: Networking &amp; Wireless
---

### Post by amitkriit on 2018-10-13
Hello,

I have been developing a network enabled application and  been testing it on 127.0.0.1 (localhost). The application is completely  memory bound, i.e. it never touches the hard disk.
Application can either use a normal TCP socket or a unix domain socket interchangeably.

Since  today morning Indian time the throughput (measured as MB/s of data  transferred) of the application running on 127.0.0.1 (localhost) slowed  down by a factor of 3.
I haven't made any changes in the application since past 5 days.

[LIST]
[*]To  be 100% sure I repeated the test with the much older versions of the  same application (up to 12 months old) and all of them exhibit a slow  down by the same factor. 
[*]To be double sure I switched the  application over to the Unix Domain Socket and there the measurement was  the same as the old results (no slow down). 
[/LIST]


**Looks like something in the kernel or network drivers dealing specifically with TCP/IP has gotten broken after the recent update**.

Is there a quick fix to this issue?

EDIT: This question is specific to Ubuntu 18.04 LTS.

---

### Post by amitkriit on 2018-10-14
Downgrading from Linux kernel 4.15.0-36-generic to 4.15.0-34-generic resolved the issue for me.
As originally suspected, something specifically dealing with the TCP/IP broke after the upgrade.

To downgrade, I pressed the ESC key repeatedly after the reboot to enter the Grub menu and selected the specific kernel (not the recovery mode) from the "Advanced options".

---

