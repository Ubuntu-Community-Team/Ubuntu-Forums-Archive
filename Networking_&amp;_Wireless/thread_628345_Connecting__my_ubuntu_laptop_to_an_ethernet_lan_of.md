---
title: "Connecting  my ubuntu laptop to an ethernet lan of windows computer"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by Alexpo on 2007-12-01
Hi, 

I am new to linux world. I have my laptop with ubuntu linux(dual boot vth XP).I want it to connect it to my office network which runs on Linux. Also I want to access Internet using the LAN.

Will you pls, guide me steps by step to achieve this task.Or refer me some links/docs.

Thanks !

---

### Post by jonandrews on 2007-12-01
I've written an illustrated guide to do  that for a mixed XP / Ununtu home network:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

It assumes a wired connection for all pc's on the network, but it may be helpful.

Let me know if it helps...

---

### Post by LisaO on 2007-12-01
Thank you very much. I've been fighting with trying to get my *gasp* windows machines to access the files on my externals attached to my ubuntu linux box. I followed your tutorial exactly one time and done. It works great.  :)

---

### Post by BrianH_1 on 2007-12-01
Yes thank you.  I have been fighting with this for a week.  Problem solved in 5 minutes.

BHH

---

### Post by BLTicklemonster on 2007-12-01
ARRRGH. 

I've been trying for two years, and I still can't network from XP to Ubuntu. 

I was hoping the guide would work, though it's exactly what I've tried before except for the -L and the enable part, yet it still didn't work.

Even did this

sudo /etc/init.d/samba reload


and it didn't work.

Here's the latest rendition of my smb.conf, though it's gone through tons of different modifications:

```
[global]


workgroup = MSHOME
security = user
username map = /etc/samba/smbusers
encrypt passwords = true


wins support = no


[Shared]
path = /home/bill/Shared
available = yes
browsable = yes
public = yes
writable = yes
guest ok = yes
```

/etc/samba/smbusers consists of:

bill = "bill"

and /etc/samba/smbpasswd has an entry in it.

I'm totally stumped.


*edit:

I take that back. I did everything except keep up with the old windows habit. I thought "sudo /etc/init.d/samba reload"  would be sufficient, but I re-read the tute, and decided what the heck, reboot.

So I now have my machine visible on the XP boxes. Thank you thank you thank you.

Whew.

---

### Post by csat on 2007-12-01
This tutorial worked for me like a charm.  Try it out.

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

