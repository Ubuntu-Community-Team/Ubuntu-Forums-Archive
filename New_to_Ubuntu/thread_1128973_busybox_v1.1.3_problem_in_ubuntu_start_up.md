---
title: "busybox v1.1.3 problem in ubuntu start up"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by gkraju on 2009-04-18
hi i am using ubuntu 8.04 (Wubi) i am using for nearly 6 months
but today during at start up it showed 

**BusyBox v1.1.3(Debian 1:1.1.3-5 ubuntu12)....etc **
so what is the problem what i have to do 
thanks in advance

---

### Post by pspsampsp on 2009-04-18
i do not know how to fix that but that means that ubuntu cant boot properly , possibly from corrupt or missing files but youll have to wait till one of the pros comes along as i might be wrong

---

### Post by jmszr on 2009-04-18
gkraju,

Wubi installs Ubuntu into a windows folder usually a NTFS type of file system. This file system has a known reaction of being unstable in other operating systems like Ubuntu.. because people sometimes fail to unmount the drive correctly, heck even Windows can be blamed for this.

Just boot into windows, then shutdown correctly and then try to boot into ubuntu as normal, everything should work. (From LowSky)

If it doesn't:
                    Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in. Click Properties.
Select the "Tools" tab and click "check now" under error checking (On Vista, You might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After the checking is done, shut down by using the start menu (Do Not hard reboot) and try using Ubuntu now. (From Ago)
                  
You can also accomplish the immediate previous tip by running chkdsk/f in Windows and then shutting down properly.

---

