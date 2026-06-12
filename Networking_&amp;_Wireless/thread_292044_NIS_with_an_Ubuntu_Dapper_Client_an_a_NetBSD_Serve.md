---
title: "NIS with an Ubuntu Dapper Client an a NetBSD Server"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by Tyler_Durden on 2006-11-03
Hi folks,
as the title might suggest I am currently trying to integrate an Ubuntu Dapper Client in a pure NetBSD environment. The main problem I am facing is that NIS is not working correctly. What does that mean?

If I try to login onto that machine, either via ssh or via console, auth.log just says:

Nov  3 14:19:42 login[2382]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty=tty1 ruser= rhost=  user=***
Nov  3 14:19:45 login[2382]: FAILED LOGIN (1) on `tty1' FOR `***', Authentication failure

The *** represent the username I am using. If I do "ypcat passwd" or "ypcat group, all is fine. However, "ypcat shadow" is not working. So, I read tons of Howtos to find out how to have the NIS server distribute shadow maps. However, even though "ypcat shadow" returns a shadow map, I am still not able to log in. What do I do wrong?

I also read that I could merge passwd and master.passwd (the shadow equivalent on NetBSD). This works, _but_ I dont want to have everybody get access to the (encrypted) passwords.

How can I integrate my Dapper box into that environment? I am absolutely clueless at this point...


Here my nsswitch.conf:

passwd:         files nis
group:          files nis
shadow:         files nis

hosts:          files dns mdns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis


The NetBSD box is: NetBSD 3.1_RC3. I dont know which version of ypserv is installed (there is no --version parameter). And no, I cannot simply replace the NetBSD machine.

Many thanks in advance for you time and help.

So long,
CU Tyler

---

### Post by Tyler_Durden on 2006-11-06
Hi,
doesn't anybody know how to solve this problem?

Many thanks in advance...

So long,
CU Tyler

---

