---
title: "System too slow as it is not using the swap partition"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by ravi_buz on 2011-05-01
I had 2 gb of swap file system when i had 10.04 and now did a clean install of 11.04. It by default created an ~768 mb og file system for Swap and my old partition was not used. I removed the second swap partition merged it with mine and created a new one and made it mountable when system start. But now when i checked my system resource, it seems my swap files are not being used. Is there any to make my system use my swap file?

below is the output of "top" command [PHP]ravi@Ravi:~$ top

top - 00:03:46 up 14 min,  2 users,  load average: 1.71, 0.93, 0.60
Tasks: 160 total,   1 running, 157 sleeping,   0 stopped,   2 zombie
Cpu(s): 15.9%us,  4.3%sy,  0.0%ni, 77.7%id,  2.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    766044k total,   455588k used,   310456k free,    11688k buffers
Swap:  2784252k total,       12k used,  2784240k free,    94680k cached
[/PHP]

---

### Post by mr_luksom on 2011-05-07
Ravi,

Swap is only used when it is needed. That particular top is showing free ram, hence the swap is not needed. If you want to test your swap, open lots of applications concurrently and try top again.

Maybe something else is causing your speed issues?

---

### Post by ravi_buz on 2011-05-08
I think since the UUID was changed after installing my swap was not used and so formatted the Swap file system using this command.

sudo /sbin/mkswap /dev/sd##

and then changed the priority and swappness value from here [https://help.ubuntu.com/community/Sw...20more%20swap?](https://help.ubuntu.com/community/Sw...20more%20swap?)

Thats all.. now my system feel faster and the swap is also used.

---

