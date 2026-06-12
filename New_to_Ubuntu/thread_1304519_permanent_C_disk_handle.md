---
title: "permanent C: disk handle?"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by Sejanus on 2009-10-29
Hi,

I just installed Ubuntu (dual boot with my Vista). Normally my Apache webdocs dir was C:\localhost (under Vista). I still can access this place as something like /media/disk-1/localhost/. What concerns me is that it seemsUbuntu mounts this disk on need-to-use basis and unmounts when its no longer needed. Does it always use the same disk-1 handle or it depends on the order in which disks are mounted or whatever else? Is it a good practice to put /media/disk-1/localhost/ to Apache httpd.conf under Ubuntu? Or is there any better way how could I keep using this directory? 

Thanks in advance for your help and please forgive my laymans terms, I'm pretty new to this :)

---

### Post by phillw on 2009-10-29
> **Sejanus said:**
> Hi,

I just installed Ubuntu (dual boot with my Vista). Normally my Apache webdocs dir was C:\localhost (under Vista). I still can access this place as something like /media/disk-1/localhost/. What concerns me is that it seemsUbuntu mounts this disk on need-to-use basis and unmounts when its no longer needed. Does it always use the same disk-1 handle or it depends on the order in which disks are mounted or whatever else? Is it a good practice to put /media/disk-1/localhost/ to Apache httpd.conf under Ubuntu? Or is there any better way how could I keep using this directory? 

Thanks in advance for your help and please forgive my laymans terms, I'm pretty new to this :)

Hi and welcome !!

I've dug out a step by step guide, using the mouse to automount your disk. Hope it's what you want !!
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Regards,

Phill.

---

### Post by Sejanus on 2009-10-29
Thanks a lot Phill, great guide! 

Just a little problem: I did install NTFS conf tool, but there's no "System Tools" under Applications. I went to System -> Preferences -> Main Menu and checked System Tools, but 2 seconds later it got auto-unchecked right before my eyes. Seems I cannot check it, it unchecks itself. Now thats pretty weird.. I can uncheck other items tho, and they stay unchecked... whats wrong with it?

P.S. I ran NTFS config tool from Terminal and it worked OK, original issue solved, thanks again :)

---

