---
title: "sftp does not work"
date: 2017-11-15
forum: Networking &amp; Wireless
---

### Post by przytula on 2017-11-15
i have ubuntu in a vmware env
Linux ubuntu 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
wanted to use ftp/sftp and followed this link :
[https://www.digitalocean.com/community/tutorials/how-to-set-up-vsftpd-for-a-user-s-directory-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-vsftpd-for-a-user-s-directory-on-ubuntu-16-04)
when I try to connect I get 
Status:    Connecting to 192.168.208.129:21...
Status:    Connection established, waiting for welcome message...
Status:    Initializing TLS...
Status:    Verifying certificate...
Status:    TLS connection established.
Command:    USER cdcadmin
Response:    331 Please specify the password.
Command:    PASS ********
Response:    530 Login incorrect.
Error:    Critical error: Could not connect to server
I use different users for whom I can logon to telnet session with that password
I also read that in /etc/passwd user needs a shell entry
if I specify this I get 
Command:    PASS ********
Error:    GnuTLS error -15: An unexpected TLS packet was received.
Error:    Could not connect to server

Any idea what I did wrong or am I missing something ?
thanks for update/help
best regards, Guy Przytula

---

### Post by TheFu on 2017-11-15
sftp works over the same port as the ssh server.  That is usually port 22/tcp.
sftp cannot be used for plain FTP connections. It doesn't work that way.

Plain FTP is on ports 20, 21 and a random port set at connection time.  Telnet should have died for connections in 1995, BTW.

So ... first ... setup ssh and get that working.  Then sftp will "just work."

And don't forget to disable all plain FTP stuff.  If some webhost is requiring plain FTP, please fire them ASAP. They are 15 yrs behind.

---

### Post by przytula on 2017-11-17
thanks for the answer
I am a DBA and not a linux admin..  just following internet docs to resolve my problems
as indicated .. I installed/configured ssh and ...  ALL OK..
many thanks for the update
best regards, Guy Przytula

---

