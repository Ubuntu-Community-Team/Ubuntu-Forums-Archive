---
title: "[SOLVED] nautilus &amp;quot;connection timed out&amp;quot; transferring large files to windows"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by jrgreoles on 2008-09-21
I am in trouble sendong large files from Ubuntu to Windows XP through LAN.

I browse with nautilus to Network -> Windows Network -> bla, bla until I reach the Shared Folder on the other PC. Everything works fine. If I send a small file, everything works out. But, when I try to transfer a large file (700 MB) it establishes the connections, stars to transfer at a 1.6 MB/s rate until I get the message "connection timed out". 

Is it a common problem? Any hints on the solution?

Thanks in advance for any hints

---

### Post by dmizer on 2008-09-22
What format is used on the target drive on the XP machine? (ntfs? fat32?)

Is there a specific size at which the connection times out?

How are you accessing the XP shared drive? (through Places > Connect to server?)

---

### Post by jrgreoles on 2008-09-22
Thanks for the reply. I finally managed to transfer the file, but it's still random to my eyes whether the transfer completes or not, so i send the info anyway.

- What format is used on the target drive on the XP machine? (ntfs? fat32?)

The target drive is **fat32**

- Is there a specific size at which the connection times out?

Not really. I've tried several times to send the same 700MB file, and the bytes received were: 252.6 MB, 246.4 MB, 700 MB, 332.1 MB ...

- How are you accessing the XP shared drive? (through Places > Connect to server?

I am accessing through Places -> Network -> Windows Network -> ...

---

### Post by dmizer on 2008-09-22
Try connecting to your shares by following the howto in my sig labeled "mount windows/samba shares ..."

fat32 drives have a file size limit of 2 gig, anything more than that will error so I thought that might be your problem. However, you indicate that the transfer is dying much earlier than that, so your problem is more likely related to how Nautilus soft mounts samba shares. Hard mounting them (as shown in my sig) will overcome that problem.

Nautilus has its purpose, and it's good for smaller files and for ease, but it just doesn't cut it for the bigger stuff.

---

### Post by jrgreoles on 2008-09-23
hey dmizer, thanks a lot for your help. Followed your guide and it worked really fine. It even increased the transfer rate from 1.6 MB/s to 2.4 MB/s.


PS: Just to let you know, I had a little problem with the nsswitch.conf part, since the line in my conf was:

> hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4


and, wherever I put the "wins" didn't work. So I just skip this step and worked anyway.

---

