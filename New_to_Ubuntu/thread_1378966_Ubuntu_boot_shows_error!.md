---
title: "Ubuntu boot shows error!"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by | Gnome | on 2010-01-12
I had a problem with Ubuntu 9.1. So, I uninstalled it and again installed 9.04 which was working perfectly fine. Now, even that 9.04 showed error after sometime without any reason. It doesn't boot (shows errors after loading). I tried Live CD and it also shows the same error (shown in attached picture). There's in no problem in the live CD. By the way, Windows XP boots fine in same system. First 9.1 and now 9.04 giving me problem. Could any one tell me what is the real problem?
Waiting for the solution...........
Thanks in advance!

---

### Post by mikewhatever on 2010-01-12
The errors look related to an hdd. Are Ubuntu and Windows on the same physical hdd?

---

### Post by kyuubi777 on 2010-01-12
I was about to say the same... i'm wondering about bad sectors on your drive atm... never mind, it looks like it's only /dev/sda7 that's effected...
maybe try partitioning that section off - resizing another and reinstalling without the use of the sda7 space on the disk

---

### Post by mikewhatever on 2010-01-12
Yeap, sda7 could be the swap partition, used by both the installation and the live cd, but not by Windows.

---

### Post by | Gnome | on 2010-01-12
Obviously I have (had) installed both OSes in same hdd.
I didn't understand one thing. I tried to live boot with Ubuntu CD and it also showed the same problem. Why does the live cd need hdd? Is their any relation? Isn't it that Live CD should boot without any concern to hdd?
Thanks!

---

### Post by HiImTye on 2010-01-12
the live CD uses any available swap space to boost its' performance.
just open a terminal and use
```
swapoff
```

---

### Post by | Gnome | on 2010-01-12
Sda7 is not swap. Here's my hdd partition acc. to ubuntu.
sda1-Windows XP
sda5 and 6- Personal data
sda7-Ubuntu
sda8-swap

I recreated both the partition (sda7 and 8) and tried the live cd. Now it worked.

I had 9.04 on sda7 and it stopped booting and showed that error out of nowhere. I couldn't even access that drive for recovering my data as live cd won't boot and windows won't detect that drive. I had to lose my data. Can anyone please tell me what really happened? How does such problem occur? It might help me in future.
Thanks!

---

### Post by kenox on 2010-01-12
Well the only partition the Livecd mounts is the swap partition. As far as i know there is nothing like a "noswap" option to prevent it from mounting this partition.

The easiest way i guess is to boot into windows go to control panel -> system tools(i hope the name is correct) and take the disk management tool.
Count the partition and identify them, linux partitions will be called "unidentified" or something. Delete the swap partition and then try the livecd again. 

Be carefull not to delete the wrong partition!!

---

