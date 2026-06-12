---
title: "Samba confusion"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by HW_Hack on 2007-03-04
I've got a fresh load of Ubuntu 6.10 on a little PC I want to use as a file server via Samba 

I've set the user folders on the server for sharing under samba --- I can see the server in the workgroup on one of the PCs --- when I click on the server workgroup share I'm prompted for user/passwd ---- I give the user/passwd that exists on the server ---- and nothing - no errors on the XP machine 

Heres the error log on the server 

[2007/03/04 00:12:29, 0] smbd/service.c:make_connection_snum(592)
  Can't become connected user!
[2007/03/04 00:12:31, 0] smbd/service.c:make_connection_snum(592)
  Can't become connected user!
[2007/03/04 00:13:55, 0] smbd/service.c:make_connection_snum(592)
  Can't become connected user!
[2007/03/04 00:13:58, 0] smbd/service.c:make_connection_snum(592)
  Can't become connected user!
[2007/03/04 00:14:07, 0] smbd/service.c:make_connection_snum(592)
  Can't become connected user!
[2007/03/04 00:14:10, 0] smbd/service.c:make_connection_snum(592)
  Can't become connected user!
[2007/03/04 00:21:20, 0] smbd/service.c:make_connection_snum(592)
  Can't become connected user!
[2007/03/04 00:21:22, 0] smbd/service.c:make_connection_snum(592)
  Can't become connected user!
[2007/03/04 00:24:30, 0] lib/util_sock.c:write_data(557)
  write_data: write failure in writing to client 192.168.2.52. Error Connection reset by peer
[2007/03/04 00:24:30, 0] lib/util_sock.c:send_smb(765)
  Error writing 4 bytes to client. -1. (Connection reset by peer)
[2007/03/04 00:24:49, 0] lib/util_sock.c:write_data(557)

---

### Post by gradedcheese on 2007-03-04
Make sure that the users (or at least yourself) are added via smbpasswd.  My [short samba guide]("http://andrey.thedotcommune.com/samba.html") explains how to do this.

---

