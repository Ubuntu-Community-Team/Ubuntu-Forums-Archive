---
title: "mysql error 2002"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by wafflcommish on 2010-01-20
Have 2 hard drives, trying to direct the data so it is on the second hard drive.  Have my.cnf and apparmor.d directed to the proper directory.  Yesterday it was working, but today I am getting an error 2002 when trying to log into mysql and Joomla will not allow me to log in.  My messages log is below:

tail /var/log/messages
Jan 20 07:46:17 server1 kernel: [ 2444.748841] type=1503 audit(1263995177.714:108): operation="open" pid=4091 parent=4090 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan 20 07:46:18 server1 kernel: [ 2445.796454] type=1503 audit(1263995178.762:109): operation="open" pid=4101 parent=4100 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan 20 07:46:19 server1 kernel: [ 2446.846487] type=1503 audit(1263995179.810:110): operation="open" pid=4111 parent=4110 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan 20 07:46:20 server1 kernel: [ 2447.890745] type=1503 audit(1263995180.854:111): operation="open" pid=4121 parent=4120 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan 20 07:46:21 server1 kernel: [ 2448.942418] type=1503 audit(1263995181.906:112): operation="open" pid=4131 parent=4130 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan 20 07:46:22 server1 kernel: [ 2449.980417] type=1503 audit(1263995182.946:113): operation="open" pid=4141 parent=4140 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan 20 07:46:23 server1 kernel: [ 2451.027431] type=1503 audit(1263995183.990:114): operation="open" pid=4151 parent=4150 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan 20 07:46:25 server1 kernel: [ 2452.091847] type=1503 audit(1263995185.054:115): operation="open" pid=4161 parent=4160 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan 20 07:46:26 server1 kernel: [ 2453.143381] type=1503 audit(1263995186.106:116): operation="open" pid=4171 parent=4170 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Jan 20 07:46:26 server1 kernel: [ 2453.186311] type=1503 audit(1263995186.150:117): operation="open" pid=4180 parent=4179 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"

---

