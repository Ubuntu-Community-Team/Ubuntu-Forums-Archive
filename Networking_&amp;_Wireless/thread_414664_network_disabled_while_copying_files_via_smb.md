---
title: "network disabled while copying files via smb"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by auditory on 2007-04-20
now i am using Feisty upgraded from Edgy yesterday.
I am not sure my problem is related to the upgrade.

Whenever I try to copy a big file (about 500MB) from windows share folder via samba,
coping is halted due to the time over. (after coping 2~300MB)

After this failure, all network functions are disabled.
I even can't reach to the dns server.

/etc/init.d/networking restart  also doesn't work.
only way i can restart the network is reboot the machine.

how can i solve this problems?

and i am afraid there is no useful info to get your help,
 how can i report more info about this issue?

---

### Post by dmizer on 2007-04-20
how did you mount your network share?

---

### Post by auditory on 2007-04-22
i just used file browser.

smb://000.000.000.000

and user name and passwd 

i didn't care about the domain name
(i don't know the domain name of windows file server)

---

### Post by dmizer on 2007-04-24
try mounting with cifs instead of using nautilus (file browser).  cifs will allow for a much more stable and reliable network connection, and allow you to transfer files larger than 2gb.  check the second link in my sig, and if you have problems post in the thread and i'll do what i can to help.

---

### Post by auditory on 2007-04-25
Thank you so much. I will try that.

Since it was urgent to use network not shutting down the machine.
i made new thread here to ask how to restart networks without rebooting,

and i found solution in other web site.

I guess this problem is related to my hardware(Marvell chipset onboard network)
and by removing and re-adding sky2.ko module
i could use network again.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/83009](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/83009)

still i couldn't use smb file transfer stabely.
i will try your suggestions.

---

