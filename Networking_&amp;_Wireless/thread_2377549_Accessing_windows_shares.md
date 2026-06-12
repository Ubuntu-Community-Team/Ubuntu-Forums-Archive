---
title: "Accessing windows shares"
date: 2017-11-14
forum: Networking &amp; Wireless
---

### Post by steve60901 on 2017-11-14
This has been maddening, I have tried everything that everything I could find on the internet suggested. The result is consistently the same "Failed to retrieve share list from server: no such file or directory. Or the one time I tried to go directly from nautilus address bar nautilus just closed lol. This is on 17.04. I set the windows computer to static ip and added the ip to the hosts file. disabled the firewall. Obviously installed samba lol, did my best to edit the smb.cfg although thats a little daunting at best. Checked sharing settings on host (windows 10) pc. Disabled entire firewall on host computer. Nothing I do seems to make a dent in this issue. 

Windows 10 (host) Ethernet
Ubuntu 17.04 5ghz wifi
samba installed
Host computer ip added to hosts file
minor editing to smb.conf
firewalls off both machines

Any information would be welcomed, i remember in previous versions of ubuntu it was EASY, just install samba and boom there ya go lol.

---

### Post by slickymaster on 2017-11-14
Thread moved to **Networking & Wireless** for a better fit

---

### Post by steve60901 on 2017-11-14
Thanks

---

### Post by steve60901 on 2017-11-14
Update, trying different "flavours" I found Kubuntu which can even tell me the name of the windows samba share but I STILL get a timeout when trying to retrieve folders...

---

### Post by steve60901 on 2017-11-15
So no one has encountered this issue or has an idea of how to fix this? Again windows share is on windows10prox64 shared individual folders as well as my storage drive. Turned off uac and firewall. checked connection type made sure it was set private and set advanced sharing settings as to not require a password and such.

Kubuntu 17.10, firewall is off. samba and wins installed. Able to see workgroup and even windows machine under network however when attempting to browse folders within machine it times out. Direct ip connect says timeout as well. It knows its there on the network but cannot browse the machine.

---

### Post by steve60901 on 2017-11-15
Update, using konsole i was able to mount the windows share and browse it.... i'd rather be able to browse it using dolphin or any built in browser but i suppose this will work. if anyone has any ideas on how to make it work through a system browser please let me know..

---

