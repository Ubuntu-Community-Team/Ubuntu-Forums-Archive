---
title: "Windows cannot access specified device, path or file  from my samba server"
date: 2014-06-26
forum: Networking &amp; Wireless
---

### Post by nathanchupp on 2014-06-26
[COLOR=#333333][FONT=Helvetica Neue]I have a problem that has developed on my user account. When I try to open any EXE file or MDB file on a network drive I get the following message.[/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]Windows cannot access the specified device, path or file. You may not have the appropriate permissions to access the item.[/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]I can open other file types without a problem - even files in the same folders as the problem files.[/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]I've double checked the permissions and I have full control on all the files in the folder.[/FONT][/COLOR]

---

### Post by Vladlenin5000 on 2014-06-26
Hi, welcome.

Installers aren't usually coded with the possibility of being run in a network drive in mind. Copy to a local drive before attempting to run.

---

### Post by nathanchupp on 2014-06-27
Thanks, 

That was not much help.. I have coded the installer to run from a network drive. I found a work around i'll just make the installer a .msi and can run it right from the server and it works fine

---

