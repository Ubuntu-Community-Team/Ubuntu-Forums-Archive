---
title: "Ubuntu 8.10 computers can't see vista shares."
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by TutonicMonkey on 2008-11-18
Looking for answers to a strange issue involving several ubuntu 8.10 computers on my home network.

Here is what I got:

Server: Vista ultra x86 on static ip 192.168.0.35
Server is sharing primary printer and backup media (several accounts each password protected)

Workstation #1: Vista x64 and Ubuntu 8.10 x64

Workstation #2: Ubuntu 8.10 x86 (sharing #2 printer)

Old Dell: Ubuntu 8.10 x86

Laptop 1: Ubuntu 8.10 x64 and vista biz x86 

Laptop 2: Vista hp x86

--------------------------------------------
**My issue is that why all the computers using vista can share and print fine to the server and the #2 printer ---- The ubuntu 8.10 computers cannot see the shared files and printer on the vista server. I can however see the workgroup and the names of all the computers on the network.**
--------------------------------------------

I found this thread on the same topic in 8.4
  
[http://ubuntuforums.org/showthread.php?t=786646](http://ubuntuforums.org/showthread.php?t=786646) 

but offers no real solutions.

It mentions printers/add: smb://(ip of windows machine) but what if this address is dynamic? 

Thanks,
Chris

Here is an image of what I'm referring to:
[IMG]http://img.photobucket.com/albums/v734/tutonicmonkey/fddfdf.jpg[/IMG]
I can see the other computers but cannot see any shared files/printers on them. (this pic is from the laptop using 8.10 x64)

---

### Post by TutonicMonkey on 2008-11-19
I found this thread this morning:

[http://ubuntuforums.org/showthread.php?t=964564](http://ubuntuforums.org/showthread.php?t=964564)

and updated samba via this post: 

[http://ubuntuforums.org/showpost.php?p=6204264&postcount=81](http://ubuntuforums.org/showpost.php?p=6204264&postcount=81)

**However it had no effect :(**

---

### Post by TutonicMonkey on 2008-11-23
update:

I found that I am able to see and access the server shares manually via: **Places/Connect to Server**
[B]
I still cannot see or print to the Printer (shared) on this server.[/B]


[IMG]http://img.photobucket.com/albums/v734/tutonicmonkey/con2serv.jpg[/IMG]



I noticed that in the Printer Configuration: Server/Settings (Show printers shared by other systems) is **NOT** checked by default.. 
[IMG]http://img.photobucket.com/albums/v734/tutonicmonkey/servrsettings.jpg[/IMG]

Checking this (and a reboot) had no effect on printer discovery.

I also ran the printer Troubleshooter and got this output:

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dests_available': [], 'cups_queue_listed': False}
Page 3 (Local or remote?):
{'printer_is_remote': True}
Page 4 (Remote address):
{'remote_server_ip_address': '192.168.0.35',
 'remote_server_name': 'chris-server'}
Page 5 (Check network server sanity):
{'remote_server_name_resolves': False,
 'remote_server_try_connect': 'chris-server'}

---

### Post by TutonicMonkey on 2008-11-26
Another piece of the pie. smbtree says everything is correct?

[IMG]http://img.photobucket.com/albums/v734/tutonicmonkey/Screenshot-chrischris-laptop.png[/IMG]

Still cannot print to shared printer :(

---

