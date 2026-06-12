---
title: "Cannot get adobe flash"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by SirKablaam on 2009-12-07
I tried to get the flash plugin for firefox on ubuntu 9.10. however when i tried it came up as > E:I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.:Then I tried to go into a terminal and used the "sudo apt-get remove flash" and heres what i got > kitty@kitty-laptop:~$ sudo apt-get remove flash
[sudo] password for kitty: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
any suggestions on how to fix this problem? Thanks.

---

### Post by rubenverweij on 2009-12-07
Have you tried something like this already: [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash).
Otherwise, try to update your archives: sudo apt-get update.
Hope this helped.

---

