---
title: "Boot problem with server"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by CarolinaGuy on 2009-03-15
I have a Boot problem with my ubuntu Hardy samba server. The system has been up and running fine for the past 6 months.

Last week the system would not shutdown with sudo halt command; so I flip the switch on the power supply.

I don't believe the boot problem has anything to do with that incident but since that time; on BOOT UP my system WILL NOT BOOT the SECONDARY IDE channel.

On a normal boot the system will not boot the secondary channel drives.

If I go into the BIOS and click on the secondary channel (Master) auto tab it will not find the drive.

If I go into the BIOS and click on the secondary channel (slave) auto tab it WILL AUTO DETECT the drive.

If I go back to secondary channel (Master) auto tab then it WILL find the DRIVE on that Channel.

YOU have to find the secondary slave before the secondary master will boot.

The system still refuse to shutdown with -- sudo halt


A7N266-C, Athlon 1800+, 512 m memory, 3 hard drive, 1 dvd drive, Ubuntu Hardy 8.04.2

THANKS,

CarolinaGuy

---

### Post by CarolinaGuy on 2009-03-17
I need to get this resolve.

Is this a MB problem or a UBUNTU problem. On BOOT-UP at the BIOS level DRIVES sdb1 and sdc1 are not detected. I have to enter the BIOS and add drive sdc1 and then sdb1 can be detected.

Can anyone HELP???

CarolinaGuy

---

