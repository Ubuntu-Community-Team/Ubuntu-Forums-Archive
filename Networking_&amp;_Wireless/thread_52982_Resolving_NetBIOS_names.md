---
title: "Resolving NetBIOS names"
date: 2005-07-29
forum: Networking &amp; Wireless
---

### Post by stwog on 2005-07-29
Hello everyone, I have 2 ubuntu systems setup at work in a Windows network. The network isn't too big, but its certainly not small. Probably about 35 computers. Usually when we need to connect to a computer in the network we can just use the name of the computer. When we are using the Linux machines this doesn't work because it can't resolve the hostnames. I know that it is possible for me to add entries to the /etc/hosts file, but that would be really bad considering the machines on the network change (mixed DHCP and static IPs) and because I don't have to do it in Windows and don't feel like I should have to. 

Does anyone know how I can fix this? 

Thanks,
Simon

PS: Adding a DNS entry for each computer in the network seems just a tedious as adding them to the hosts file so I don't want to do that.

---

### Post by stwog on 2005-08-03
Judging by the lack of responses this this thread, there is no way for Linux to do this... 

It seems strange that I am the only one that seems to care about this feature. To bad.

---

### Post by robmoore on 2005-08-30
From [http://lists.samba.org/archive/samba/2002-October/053697.html:](http://lists.samba.org/archive/samba/2002-October/053697.html:)

Edit your /etc/nsswitch.conf file so it has: hosts: files dns wins

HTH,

Rob

---

### Post by stwog on 2005-09-22
I just remembered that I posted this message a long time ago and thought I would check up on it...

Your solution worked perfectly!! Thank you so much!

---

