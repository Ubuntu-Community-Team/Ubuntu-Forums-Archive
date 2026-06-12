---
title: "gutsy: samba not working with hostname, ip address only"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by meowsqueak on 2007-11-15
I recently upgraded from feisty to gutsy. Everything seemed in order except one issue:

I can no longer access my HOME samba share (on my gutsy box) from my Win2k terminal server if I use the hostname (e.g. "myserver") of my gutsy box. If I use the IP address directly (10.16.xx.xx) then it seems to work. My non-HOME shares work fine and other people can access them too.

The error that Win2k reports is a dialog: "\\myserver\user is not accessible. The network path was not found. [OK]"

Any ideas why I cannot access my shared home directory unless I use the numerical IP address?

Note I have tried various things like restarting samba and the win2k terminal server. 
I have checked I have 'security=user' in smb.conf. 
Enabling 'wins support' does not help.
My IP address has not changed. 
My /etc/hosts has a valid reference to itself. 
This all worked perfectly with feisty.

---

### Post by crmanski on 2007-12-18
I upgraded last week and I had the same problem too. I have an active directory.  I found that using the fully qualified domain name worksthough....
\\myserver.mydomain.com

---

