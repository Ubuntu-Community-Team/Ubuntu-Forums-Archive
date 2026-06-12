---
title: "Samba login: works with Ubuntu, not with Windows XP"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by Diskdoc on 2008-10-08
I'm having headaches setting up Samba.. I have a share that is to be available to only a few users using their own login/password. It works perfectly from Ubuntu clients but not from Windows XP clients.

Checking the logs, I see this:

[2008/10/08 16:28:07, 4] smbd/reply.c:reply_tcon_and_X(506)
  Client requested device type [?????] for share [GEMENSAM]
[2008/10/08 16:28:07, 3] smbd/service.c:find_service(286)
  checking for home directory gemensam gave (NULL)
[2008/10/08 16:28:07, 3] smbd/service.c:find_service(296)
  checking whether gemensam is a valid printer name...
[2008/10/08 16:28:07, 3] smbd/service.c:find_service(306)
  gemensam is not a valid printer name
[2008/10/08 16:28:07, 2] smbd/service.c:make_connection_snum(605)
  guest user (from session setup) not permitted to access this share (gemensam)
[2008/10/08 16:28:07, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/reply.c(514) cmd=117 (SMBtconX) NT_STATUS_ACCESS_DENIED

Why can't the Windows clients connect?

---

### Post by Diskdoc on 2008-10-08
*later*

Well. I have a very puzzling situation, trying to get these Windows XP-clients to work. Listen to this:

Client A is Windows XP Home
Client B is Windows XP Professional

Both are trying to access a password (and user) protected SAMBA-share. Both are using administrator-accounts.
Client A asks for username and password and succeeds.
Client B asks for username and password and fails (see above).

When browsing for shares, Client A asks for username/password to show shares on the SAMBA server. Client B requires no username/password to show a list of the SAMBA shares.

Furthermore, both clients can access a public share without problems.

Client B CAN access the private share but ONLY if the IP of the server is entered manually (\\192.168.2.163\private).

WHY is this???!:confused::mad:

edit: The difference between A and B in asking for username/password when browsing for shares could be that the account on A did not have a password set for the account (not my computre btw..). When I tried another administrative account with a set password on A, it too now displayed the shares on the SAMBA server when browsing for them.

---

### Post by superprash2003 on 2008-10-08
what is the output of cat /etc/samba/smbusers

---

### Post by Diskdoc on 2008-10-09
I have no such file!

---

### Post by superprash2003 on 2008-10-09
thats why you have authentication problems.. follow step 5 here [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

