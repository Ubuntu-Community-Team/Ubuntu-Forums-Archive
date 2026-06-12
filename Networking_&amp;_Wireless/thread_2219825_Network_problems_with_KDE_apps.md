---
title: "Network problems with KDE apps"
date: 2014-04-25
forum: Networking &amp; Wireless
---

### Post by kleinempfaenger on 2014-04-25
Hi, 
KDE apps don't find the Workgroup on my network. I have some folders shared over nautilus-share on Ubuntu 13.10. When I open Digikam, it won't find this network. Installed Smb4k and after netscan shows WORKGROUP, when I click on it disappears.

I share an external HD over the network. Tried to delete folders with strange caracters. 
Is there a solution?

---

### Post by SeijiSensei on 2014-04-25
Can you open the share from Dolphin by entering an smb URL in the address box like this:
```
smb://ip.of.the.server/share
```
If not, try adding "user@" in front of the server's IP, or "user:password@"?  If so, can you then open the folder with Digikam from Dolphin by right-clicking and choosing "Open With?"

---

### Post by kleinempfaenger on 2014-04-26
Thanks for your reply. I changed plans. Smb4k seems to be a bit buggy on Ubuntu and I realized, that I could reach the HD from Digikam over the network. But the data-transmission would be too slow, which might leed to errors and low performance. So I connected the HD directly. I will have to move it around sometimes, but I prefer this.

---

### Post by SeijiSensei on 2014-04-26
Connecting it directly would have been my next suggestion!

---

