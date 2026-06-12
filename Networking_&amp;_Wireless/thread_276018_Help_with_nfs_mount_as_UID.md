---
title: "Help with nfs mount as UID"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by knichel on 2006-10-12
I am trying to mount a nfs share using a specific UID from the server.  On the server 192.168.6.30 I am sharing /home/DropBox using rw.  I have an account on the server with UID=1000.  I wish to mount this share on my laptop, but not as root.  I wish to mount as my account on server (UID=1000).   My UID on laptop is not 1000.

My laptop requires mount run as root.  What is the command to mount this share so I can get appropriate permissions (rw-) on folder?

I have tried to man mount and figure it out, but have been unsuccessful.

Thanks in advance.
Mike

---

