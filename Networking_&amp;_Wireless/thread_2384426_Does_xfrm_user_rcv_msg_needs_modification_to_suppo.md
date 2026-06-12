---
title: "Does xfrm_user_rcv_msg needs modification to support 32 bit IPSec on Ubuntu 16.04"
date: 2018-02-07
forum: Networking &amp; Wireless
---

### Post by bhatja on 2018-02-07
[COLOR=#000000][FONT=Verdana]Hi All,[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I am in the processing of migrating IPSec app from VxWorks to Linux. And I am pretty new to Linux environment. Component that uses IPsec is a 32 bit application, however entire product runs on a 64 bit environment. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]We are using Ubuntu 16.04 (LTS) on X86_64 bit machine. Linux kernel version is 4.9. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]32 bit IPSec on 64 bit kernel had incompatibility issue with respect to structure padding in xfrm.h. This was an easy problem to fix. However after fixing this issue I was not able to install SA's. XFRM framework was returning -95 not supported error. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]After debugging I found below check was creating the issue. I commented the API just for testing. After rebuilding the kernel with this change 32 bit IPsec app worked fine on 64 bit kernel. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I wanted to understand is this a buggy code for X86_64 architecture? [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]#ifdef CONFIG_COMPAT[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]if (in_compat_syscall())[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]return -EOPNOTSUPP;[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]#endif [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Regards[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Jayalakshmi[/FONT][/COLOR]

---

