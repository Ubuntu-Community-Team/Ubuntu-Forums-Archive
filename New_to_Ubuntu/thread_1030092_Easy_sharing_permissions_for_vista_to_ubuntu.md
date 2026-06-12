---
title: "Easy sharing permissions for vista to ubuntu?"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by wespawloski on 2009-01-04
I am interested in providing an easy way for my ubuntu configuration to access a windows network share. currently I have to enable "Everyone" as a vista group to automatically view the share from ubuntu but this is not entirely favorable. Do I have to use this Samba? I'm depressed I cant just open a mount and provide a username and password via dialogue box as windows to windows configs communicate and or some easy login with terminal or the like. If anyone has any suggestions or thoughts I would greatly appreciate it!

Thank you in advance

---

### Post by MenZa on 2009-01-04
I believe you can do this with password authentication. Try Places &#8594; Connect to Server... and chose 'Windows Share', inputting a username and password.

Samba is a service to run on Ubuntu to share files with other computers---e.g. your Linux server would be the host.

---

### Post by wespawloski on 2009-01-04
Well thank you very much for pointing that out, although its not quite as easy and i'll have to do some tinkering :P but I believe I can figure it out. In the examples I found Samba was used, in conjunction with mounting and a loadable username/password combo but that seemed excessive for what I was trying to do. 
The method via 'connect to' seems to be a straightforward way, thank you.

---

