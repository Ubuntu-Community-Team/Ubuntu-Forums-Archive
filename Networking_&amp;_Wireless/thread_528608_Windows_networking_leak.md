---
title: "Windows networking leak?"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by benxp on 2007-08-18
When I browse computers in the network and know their Username/Password, I can access all the files in the hard drive eventhough the drive is not "Shared". I can even access our office LAN server computer. Why is this happening?

The said computers use Windows operating system. While my personal laptop uses Ubuntu & Windows.

Can anybody explain this though I was amazed of what I discovered. Since I thought our LAN is secured.

---

### Post by TorbX on 2007-08-18
How can you access the files?

---

### Post by Synflux on 2007-08-18
Are you sure you don't have the default admin shares enabled? Windows automatically creates some shares which it marks as 'hidden' by putting a $ sign after the share name. Common ones include:

C$, D$ etc (your local drives)
admin$ (your windows directory)
print$ (for printer drivers)
IPC$ (for remote IPC)

There are whole books on securing windows file sharing as there are many pitfalls to be aware of. If you're concerned I'd check the following as a minimum:

1) Right-click My Computer and click Manager, browse to the Shared Folders->Shares option which lists all the active shares on that computer. Here you can set the permissions for each share.

2) In Windows Explorer go to Tools->Folder Options and click on the 'view' tab. Look right at the bottom and make sure that 'use simple file sharing' is not ticked. I think this only applies to XP from memory.

If you're still worried about it then try [COLOR="DarkRed"][Nessus]("http://www.nessus.org/download/")[/COLOR] which can scan your hosts for thousands of vulnerabilities and suggest solutions.

:)

---

### Post by benxp on 2007-08-25
Thanks..Im gonna check it..

---

