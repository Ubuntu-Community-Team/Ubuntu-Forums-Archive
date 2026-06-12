---
title: "Ubuntu Server - Shutdown Alert Message"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by rlross4455 on 2008-02-14
When the Server is Shutdown or Shutdown Reboot, the messasge that is sent to the workstations
is not shown on the network workstations.

Thank You

---

### Post by dca on 2008-02-14
If a user is shelled into that server when the command is issued they should see the warning...  Is someone accessing through another type of service and not getting the message?  I think the command to send little messages to user logged in is 'write'

---

### Post by rlross4455 on 2008-02-14
First of all, i am running an NFS file system Server on Ubuntu Server. I thought that when users have
connected to mapped shares of the server, that for any reason the server was going thru or about
to go thru a shutdown, all the users connected to these shares would recieve this message.

---

### Post by tgalati4 on 2008-02-14
I think only those logged into shells get the message since the message is broadcast to terminals.  I don't know if fuse or smb shares behave differently from nfs.

---

### Post by rlross4455 on 2008-02-15
Thanks**_ tgalati4 _**and **_dca_** for your help with this matter. You both were correct, in that the message in deed come thru only when you are shelled into the server terminal.

Thanks Again For your Help:)

---

