---
title: "Unable To See Windows Network Shares"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by dater on 2008-07-14
OK, I have been working on this for hours and reading other threads, and googling, to no avail.

My problem since moving to Hardy is that I can no longer see my Window XP machines in Places/Network/Windows Network. 

This is not a Window to Ubuntu issue, but a Ubuntu to Windows issue. I have shares on my Windows XP machines and have been able to peruse the shares when I was on Gutsy. 

From what I have read, Ubuntu should be able to see Windows shares out-of-the-box, however Windows to Ubuntu requires Samba configuration.

Any ideas?

---

### Post by superprash2003 on 2008-07-15
in your terminal type nautilus smb://x.x.x.x where x.x.x.x is the ip of the windows machine

---

### Post by dater on 2008-07-15
> **superprash2003 said:**
> in your terminal type nautilus smb://x.x.x.x where x.x.x.x is the ip of the windows machine

Thanks for the feedback.
I tried that. It opened Nautilus, but it was an empty window. No message, no nothing. Is there any smb logging that might help to troubleshoot? I have checked /var/log/messages, etc. Nothing found so far.

TIA!

---

### Post by rbc on 2008-07-15
Try typing the whole path to the share:
smb://x.x.x.x/Users/username/MyDocuments/MyPictures (or whatever it might be for you)

---

