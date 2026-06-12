---
title: "I need a TFTP server"
date: 2005-08-31
forum: Networking &amp; Wireless
---

### Post by i_spock on 2005-08-31
Hello everyone!  I'm new to ubuntu looking for a good tftp server.  I'm a network guy so I want to use it for router upgrades, config changes, etc. 

 As far as I can tell, one isn't included with the distro.   Can anyone recommend a good tftp server? 

Thanks!
Dan

---

### Post by DJ_Max on 2005-08-31
There are about three in the repositories.

In Synaptic, search for *tftp*. (Make sure you have the [extra repositories](http://ubuntuguide.org/#extrarepositories).)

---

### Post by i_spock on 2005-09-02
Thanks! I found atftpd and it works great..

---

### Post by DJ_Max on 2005-09-02
[QUOTE=i_spock]Thanks! I found atftpd and it works great..[/QUOTE]
No problem. I've heard of TFTP, but never actually knew what it was for. Seems like you learn something everyday.

Regards

---

### Post by Dry Heat on 2006-01-24
OK.  I'm in the same situation.
How did you configure atftpd to work?
I'm currently running in.tftpd under inetd.
Netstat says it's listening.
However, when I try the old "copy run tftp" while on a Cisco device, it won't write anything.
I can ping my laptop from any device, so some communication can get through.
Can you offer any details on your install?

Thanks.

---

