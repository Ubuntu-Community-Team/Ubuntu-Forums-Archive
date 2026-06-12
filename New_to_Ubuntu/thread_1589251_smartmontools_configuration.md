---
title: "smartmontools configuration"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by node2network on 2010-10-06
Hi, i want to check HDD health by using smartctl.

I did below command.
```
$ sudo smartctl -t short
```

I got below result.
```
# 1  Short offline       Completed without error       00%       348         -
```

From this result, my HDD is healthy. So, I try to check HDD health routinely.

I think a lot of HDD health logs are useless. 

I want to delete the logs, but the logs remains after reinstalling os.

Where is the logs? How to delete the log?

help me!

---

### Post by Paddy Landau on 2010-10-06
I believe that the drive itself stores this information.

> The smartmontools package contains two utility programs (smartctl and smartd) to control and monitor storage systems using the Self-Monitoring, Analysis and Reporting Technology System (S.M.A.R.T.) built into most modern ATA and SCSI hard disks.You can use a GUI to access this information. System > Administration > Disk Utility. Click on the drive, and on the right-hand side you'll see "SMART Data". I think this is the same thing.

You don't want to delete that information, and possibly you can't.

---

### Post by node2network on 2010-10-06
Thank you for your reply.

HDD storage capacity is limited. So, the logs fill up HDD storage in the future.
The old logs are not necessary, aren't you? I want to delete the logs.

---

### Post by psusi on 2010-10-06
The log is stored in the drive itself, can not be cleared, and does not use up disk space, so don't worry about it.  It only has room for something like 10-12 and then the oldest ones fall off the end.

---

### Post by node2network on 2010-10-06
Thank you for your reply.

Wow!

The logs does not use up disk space!

---

