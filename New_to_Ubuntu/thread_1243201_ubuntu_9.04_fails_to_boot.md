---
title: "ubuntu 9.04 fails to boot"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by bipin.nag on 2009-08-18
i had recently installed ubuntu inside windows vista and it did run succesfully at first but now it does not boot to logon screen

during boot when loading hardware drivers it shows messages like

[        10.007320] xd 6:0:0:0: [sdb] Assuming drive cache :write through
.......


and then

20.1291701 /build/buildd/linux -2.6.28/drivers/............        failed
.........


then the screen goes blank, blinks a few times before hanging up

before this problem started i was trying to update my video drivers
i work on a dell studio 17 laptop

any help on this matter is welcome. i dont have any experience working on ubuntu and i dont want my system to crash or to loose data from ubuntu installation

or can anyone tell how can i restore original video drivers

please help!!
:cry:

---

### Post by riazrahaman on 2009-08-18
try booting into failsafe mode and capture the boot logs from /var/logs location.

I am not sure if the older logs get over written. If it is mostly a driver issue then you could try uninstalling the driver from failsafe mode.

---

### Post by bipin.nag on 2009-08-19
:(
no results
had to reinstall ubuntu

---

