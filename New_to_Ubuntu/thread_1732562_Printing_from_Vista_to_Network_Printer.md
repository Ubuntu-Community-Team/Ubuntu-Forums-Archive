---
title: "Printing from Vista to Network Printer"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by darkeale on 2011-04-18
Hi,

I have Ubuntu Server 10.04.2 installed on an old computer.  I have set up my Epson CX5400 printer on it and can print fine from Ubuntu Server.  I want to set it up as a network printer to be able to print over the network from my Vista laptop.  I can see the printer in Vista, and following advice elsewhere, I installed the Vista drivers in Vista.  It allows me to select the printer, but nothing actually prints.  When I check the CUPS job list, there is nothing there from Vista.  The jobs don't show up at all.  Does anyone know what is causing this problem?

Many thanks,
Alex

---

### Post by darkeale on 2011-04-18
ok, I don't know why but it has started working!  All I have to do is SSH into the server, then restart smbd using:-

sudo service smbd restart

Does anyone know how I can set it up so that as soon as I turn on the server and it has booted I can print, without having to SSH into and restart the Samba service?

Thanks,
Alex

---

### Post by Morbius1 on 2011-04-18
Actually smbd was already started. Had it not been and you issued a "sudo service smbd restart" you would have received the following error message:
> Unknown instance The problem as far as I can make out is that CUPS is starting after SMBD starts. Cups has to start first in order to provide samba with the printer list when it starts.

There's a bug report on this problem here: [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/494141](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/494141)

The workaround at the moment seems to be to add a line ( before the exit 0 line ) to /etc/rc.local that restarts samba and forces it to read the printer list from cups:
```
service smbd restart
```Or as suggested in the bug report:
```
service smbd reload
```

---

### Post by darkeale on 2011-04-18
Thanks a lot!  That has solved it.

Alex

---

