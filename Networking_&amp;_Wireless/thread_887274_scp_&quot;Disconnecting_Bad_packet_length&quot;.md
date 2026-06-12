---
title: "scp &quot;Disconnecting: Bad packet length&quot;"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by thornelawler on 2008-08-12
I have a serious problem with scp which has only cropped up in the last 48 hours or so. Prior to that, scp between these systems had been working fine.

client: 
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
(Ubuntu Hardy, updated to current today).

server: 
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
(Ubuntu Hardy server, updated to current today).

When I attempt to scp any file larger than a few kilobytes from the client to the server or vice versa, only a small part of the file (~10kb to ~300kb in tests so far) is actually copied. The client shows '100%', but does not complete. After a long time, the client terminates with a message like the following:

Disconnecting: Bad packet length 3613810137.
debug3: channel 0: close_fds r 4 w 5 e 6 c -1
lost connection

This fault is 100% repeatable.

Has anyone seen anything like it? Any suggestions? 

If nobody has any ideas, I will log this as a bug.

---

