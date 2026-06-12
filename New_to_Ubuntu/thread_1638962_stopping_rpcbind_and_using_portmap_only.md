---
title: "stopping rpcbind and using portmap only"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by srjlinux on 2010-12-06
Hello, 


  I am a beginner in terms of using the ubuntu desktop. Need help to stop rpcbind, 
the portmap service was working properly and I just tried to install rpcbind and then found that if stop rpcbind using /etc/init.d/rpcbind stop, the portmap is completely gone. 

   If I try to install portmap again it gives me error.

  Presently, I am this infromation from my desktop,
  user@user-laptop:~$ rpcinfo -p
   program vers proto   port  service
    100000    4   tcp    111  portmapper
    100000    3   tcp    111  portmapper
    100000    2   tcp    111  portmapper
    100000    4   udp    111  portmapper
    100000    3   udp    111  portmapper
    100000    2   udp    111  portmapper
 
 user@user-laptop:~$ /etc/init.d/rpcbind status
 * rpcbind is running


I want to stop rpcbind and use portmap only, as some of my FUSE application is not working properly because of rpcbind.

Please provide some solution to this issue.

Thanks in advance, 

Regards,
srjlinux

---

