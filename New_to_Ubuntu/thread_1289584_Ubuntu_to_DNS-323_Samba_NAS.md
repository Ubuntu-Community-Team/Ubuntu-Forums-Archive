---
title: "Ubuntu to DNS-323 Samba NAS"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by msimon1960 on 2009-10-12
I have a Ubuntu 9.04 fresh install connected to a Dlink router -- static addresses for all workstations.

The server is s Dlink DNS-323 Samba 3.x server.

When I click Places->Network I instantly see the 'Windows Network' icon.  

When I click on it and I see my workgroup 'SLIPKNOT'

When I click on 'SLIPKNOT' I see my DNS-323.

When I click on 'DNS-323' it won't open.

I can connect to the shares on the DNS-323 (e.g. Volume_1) without difficulty using a Windows share IF AND ONLY IF I use the ip address of the DNS-323 AND NOT THE NAME.

Any idea why the GUI cannot connect to my DNS-323 shares?

---

### Post by noelvh on 2009-10-12
I have no idea how to get the network browser to work! I have tried for a long time with no luck!! But I still have access to my shares on windows machines. From you file browser goto connect to server do a smb://ipaddress\sharename and see if it connects. Then you can edit you fastab to auto mount on boot up of the system.

Noel

---

### Post by msimon1960 on 2009-10-12
Found the problem:

For some reason the system doesn't resolve the name of the server into an ip address.  No IP and no connection.

Edit the hosts file as follows:

From the Terminal program:

sudo gedit /etc/hosts

add a line to show the IP address of the server.  In my case:

192.168.1.20  DNS-323

save the file.  Close terminal and reboot.  You should be able to browse the windows shares now using the GUI.

Someone needs to fix the name resolution system in Ubuntu networking for windows shares.  Seriously...

---

### Post by yobib on 2009-11-26
This worked, thanks a lot!

---

