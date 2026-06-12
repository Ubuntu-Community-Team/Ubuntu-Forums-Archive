---
title: "[SOLVED] Simple way to connect access files on main XP pc from laptop please"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by zenithdave on 2008-12-26
Hello, as the title says really?? i just need to connect and pull files off  my main XP pc via wireless?

The wireless computer is running ubuntu-eee

Im behind a router and can use the ip address.

thanks in advance

---

### Post by nhasian on 2008-12-26
if you have files shared on the WindowsXP you should be able to see it from Places->Network->*WindowsXPComputername*  if you dont see the windows computer disable any firewalls that may be running on it and try again.

---

### Post by zenithdave on 2008-12-26
wow! thank you, working just fine now :)happy new year :D

---

### Post by zenithdave on 2008-12-26
Could you help me a little more? in Ubuntu i can go windows networks/MY WORKGROUP NAME but i cannot see any shared files?

XP is set up to share as far as i know (hands under folders)

Nearly there :D..

thanks

---

### Post by superprash2003 on 2008-12-26
you could try accessing windows shared folders by typing smb://x.x.x.x where x.x.x.x is the ip of the xp machine.. do this in nautilus [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by HermanAB on 2008-12-26
There are various methods to share files over a network.  In order of increasing difficulty:
a. FTP (requires FileZilla)
b. NFS (requires Windows services for Unix)
c. SSH (requires Cygwin)
d. Samba (native Windows networking)

So, if you want a simple and no-nonsense way of sharing files, go to the FileZilla web site and install the server and client on Windows.

---

### Post by zenithdave on 2008-12-27
superprash2003 that worked great thanks, very nice :D :)


HermanAB Ill now try to setup filezilla, im half way through. 

Thanks again very much, fast response ..

:guitar:

---

### Post by zenithdave on 2008-12-27
Thanks again helpers :D i now have a fully functioning ftp system (filezilla) between my XP-pc and Ubuntu :) top job thanks again, happy new year. :guitar: really appreciate it.

Just one more question, ami safe to share my whole C drive across the wireless ftp?, i am behind a NATS router?

---

