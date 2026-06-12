---
title: "Unable to connect to SMTP In Thunderbird"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by newgalois on 2007-06-05
Hi, I've just installed Ubuntu and Thunderbird, but I cannot connect to SMTP server. I tried two SMTP server of my school, and one of gmail. All of them use SSL and none of them use port 25. But Thunderbird always times out when connecting to the SMTP server. I tried Evolution too, but it didn't help. On the other hand, I can connect to the IMAP server. 

I searched this forum and found some threads, and everyone seems to talk about firewalls. However, both firehol and firestarter are not installed in my computer. I did "ps -ef | grep fire" and found nothing. 

Any idea?

Thanks,

---

### Post by jglen490 on 2007-06-05
I know that gmail has some very specific instructions for connecting a mail client such as T-Bird.  I had to set my wife's computer up with T-Bird and Gmail.  One of the things that was necessary was changing the port.  Similar instructions may also be available for your school email servers.

---

### Post by linfidel on 2007-06-05
Have you ever connected to any of these servers with another system?  Many ISPs will not allow you to connect to an outside SMTP server, so you need to use theirs.  This is due to spyware on computers sending out spam, I think.  Have you tried connecting to your ISP's server, or are you using the school's?

Did you set up the authentication with your name and password?  This is not always on the main page, since it's not always needed.

---

### Post by newgalois on 2007-06-05
Actually, I forgot to mention that I installed Ubuntu on a virtual machine (VMWare) on a Windows box. I can connect to all the smtps mentioned above by thunderbird on the host machine. I also have another virtual machine machine on the same host which runs Windows XP, and thunderbird connect well to all the smtp servers on this virtual machine. Also, the IMAP servers worked just fine even on the Ubuntu virtual machine. I don't think the problem is caused by gmail, as it happenned to my school email too.

---

