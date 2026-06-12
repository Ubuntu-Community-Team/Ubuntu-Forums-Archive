---
title: "ubuntu server problems"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by jpschubert on 2010-04-15
When I install server 9.10 using a manual partitioning scheme for LVM, I get a message GRUB loading error: no such disk but server continues to boot and seems to do so successfully. When I installed 9.10 without LVM I didn't get this error message. I don't know enough to decide if this is a problem I should be worried about to complete all the customization to my server I want or not. Does anybody know why this is happening and what I can do to fix it? I also get an error when running ifconfig /all sayinf error fetching interface information :device not found. I found this when trying to find the ip address of my nameserver so I could complete staitc ip setup for this server.

---

### Post by Jon Monreal on 2010-04-16
I don't believe it's anything to be worried about.

Since [this thread]("http://ubuntuforums.org/showthread.php?t=1422988") seems to deal with a similar problem, perhaps you could try disabling USB and network boot and seeing if that makes it go away.

---

