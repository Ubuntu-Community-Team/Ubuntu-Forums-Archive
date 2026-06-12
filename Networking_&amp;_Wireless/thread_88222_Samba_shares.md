---
title: "Samba shares?"
date: 2005-11-09
forum: Networking &amp; Wireless
---

### Post by Mantrasong on 2005-11-09
I installed samba and smbfs, but when I went to Network servers and clicked on Windows Network, it opens, but it doesn't show anything. I also don't have a "window's networking" pane in my network settings.

How do I set up samba so I can view/ mount other window's shares?

---

### Post by frodon on 2005-11-10
There's a nice HOWTO about it, it might help you : [http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba](http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba)

---

### Post by Mantrasong on 2005-11-10
I followed the tutorial all the way through, and I see a network folder in my home folder, but I still do not see any shares? Am I missing something?:(

---

### Post by frodon on 2005-11-10
Do you have a firewall, a router, are you using wifi ? 
It might be the problem.

---

### Post by Mantrasong on 2005-11-10
I don't have a firewall running, but I'm on a school network, with the ethernet coming through a switch.
If this helps, when I try to open the network folder it trys to load for a while, then it comes back with the error "The folder contents could not be displayed./Sorry, couldn't display all the contents of "Network"."

Edit: when I try to "ls" it in terminal, it comes back with "reading directory .: Input/output error"

---

### Post by Mantrasong on 2005-11-11
Can anybody help me solve this?

---

### Post by LinuxWiz83 on 2005-11-11
The school network is probably running a router or some type of hardware firewall.

---

