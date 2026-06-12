---
title: "Ubuntu seeing Debian"
date: 2006-07-29
forum: Networking &amp; Wireless
---

### Post by tripwire45 on 2006-07-29
I'm playing around with my new Ubuntu 6.06 VM and so far I'm quite impressed. I've loaded Macromedia Flash 7 for Linux in Firefox, I can print, play music and do just about all of my normal tasks.

I am puzzled by one thing. I can navigate to other Windows boxes on my network by clicking Places -> Network Servers.. A box appears with icons for each computer on the LAN/WLAN plus a Windows Network icon appears, but no Linux machines, even though I have a Debian (not a VM) machine on the same network.

What gives?

I should mention that the machines can ping each other.

---

### Post by john_spiral on 2006-07-29
try sharing a folder on the debain machine.

---

### Post by tripwire45 on 2006-07-30
I suspect the issues is that samba is enabled on both linux machines but not nfs. Hence the ability for linux to see windows but not linux. I'll noodle around and see what else I can discover, thanks for the response, john_spiral. :)

---

### Post by tripwire45 on 2006-07-30
Well...it's getting better. I shared a folder on the Ubuntu machine using NFS. Then I got on the Debian machine and tried to navigate to it. In the network box, I can see two Windows machines and Windows Network. When I open Windows Network, I see the Windows Workgroup and "mshome", which wasn't there before. I open mshome and can see the Ubuntu machine but when I open it, the window is blank registering "0 items".

Oh well...back to the drawing board.

---

### Post by john_spiral on 2006-07-31
Check the permissions on shared file?

---

