---
title: "Samba Prob"
date: 2005-10-04
forum: Networking &amp; Wireless
---

### Post by shikamaru5314 on 2005-10-04
Hi I have a prob.
I have a office LAN workgroup name = mshome :
4 Windows 2000 
2 Win98
2 Winxp
1 laptop WinXp
all of it p*rated.
So as a legal solution I propose using Linux ( Ubuntu) and do OpenOffice  training per user basis.
The solution :
1 Ubuntu server (LinuxServer : 192.168.3.1) as a dns and Samba server and system demo.
(Workgroup style networking must be enabled)
Change other comp to Linux slowly and training per user basis.
(Workgroup style networking must be enabled)
The senario :
1) I set up the DNS server using BIND9. Only have  LinuxServer  in DNS mapping.
2) Set up Samba with minimal conf :
Prob :
a) Browse using WinXp laptop on -->workgroup see LinuxServer as 
Samba 3.0.10-Ubuntu (LinuxServer). Is this correct ?. 
According to tutorial I should see LinuxServer directly.
b) Do a search 192.168.3.1. on WinXp. Returned "192.168.3.1 in Unknown".
Is it supposed to return "LinuxServer(192.168.3.1) in mshome" ?
c) Certain computer produce both localhost.localhost and Samba 3.0.10-Ubuntu (LinuxServer)
My theory :
a) to use Dns server so prob b is corrected.
b) Using LinuxServer as a Samba Server, So every other comp can see LinuxServer and others. But the prob a persists.
Where I did wrong ?
Linux Conv here:D . Thanks in advance

---

### Post by mlomker on 2005-10-05
I don't have any experience with this yet, but have you gone through [the wiki]("https://wiki.ubuntu.com/SettingUpSamba") on setting up samba?

---

### Post by shikamaru5314 on 2005-10-05
Yes I had.

Apparently if I set up samba its working. I can see those other Win PC, and they can see linuxserver. However when I ping from Windows PC to  linuxserver it fail. that is why I need DNS server. 

Or my settings is incorrect.

---

### Post by mlomker on 2005-10-06
> that is why I need DNS server. 


If it is a small network then you could just add entries to the **hosts** file on each machine instead of configuring DNS.  The file is c:\windows\system32\drivers\etc\hosts on Windows and /etc/hosts on linux.

---

