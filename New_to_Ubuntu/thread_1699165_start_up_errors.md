---
title: "start up errors"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by wordmaster on 2011-03-03
I am running 10.04 and when I boot, it goes through, at a guess, 50 or more errors all similar. They flash by too quickly to get a good reading, but they are something like

a long number...end-request... IO error...dev SR0 sector (varies)

Any help appreciated

---

### Post by maqtanim on 2011-03-03
What is the result of those errors? Are you able to run Ubuntu? Or do you face any problem after running Ubuntu?

---

### Post by JKyleOKC on 2011-03-03
I get that also on one of my systems that seems to have a problem with its CD drive. The "SR0" refers to the CD drive's internal device identifier assigned during the boot process.

Apparently the boot process is attempting to establish communication with the drive, and getting an error when doing so. It then tries again, and this continues for some 30 seconds in my case. That long number at the start is the count in seconds since the boot began, for each message.

Once it stops, everything seems to work except that the CD drive doesn't seem to be in the system. I'm assuming that it has either gone bad (although the Win98 dual boot system on that box does not have a problem with it) or is simply not recognizing the command that the boot program is trying to send it.

I've even gone into the BIOS setup and told it that the drive is not connected, but the boot code still tries to check it! Removing any disk from the drive cuts the attempts from 30 seconds down to just a couple, though...

EDIT: You can go to the /var/log/syslog file and scroll through it to view the exact error messages if you want to verify the details...

---

