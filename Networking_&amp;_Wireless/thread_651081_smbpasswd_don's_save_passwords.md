---
title: "smbpasswd don's save passwords"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by Ailandar on 2007-12-27
First, I'm apologize for my bad English.

I'm have a problem. I'm have home network: Kubuntu 7.10 computer, Mandriva 2008 and Windows XP Home SP2 (laptop) ones. Mandriva and Windows gives access to their shared resources and can connect to other. Kubuntu computer can access to resources of other computers, but don't give access to own folders and files. It ask login/password (even if I want to be connected from itself). I adjust access by means of smbpasswd. A command is executed, but a record in a file /etc/samba/smbpasswd is not made (a file is opened for a record!). It is command out:

> Old SMB password:
New SMB password:
Retype new SMB password:
Could not connect to machine 127.0.0.1: NT_STATUS_LOGON_FAILURE
Failed to change password for nestor

If to do it through sudo, error diagnostics is not present, but also a record in the file of /etc/samba/smbpasswd is not made.

What can I do?

---

### Post by zero-9376 on 2007-12-27
i think when i do my setup i use

sudo smbpasswd -a username #to add the user
enter the new password
sudo smbpasswd -e username #to enable the user

then maybe restart samba

sudo /etc/init.d/samba restart

---

### Post by Ailandar on 2007-12-27
I did it. /etc/samba/smbpasswd file after these operations is empty.

---

### Post by zero-9376 on 2007-12-27
im on gutsy and i dont actually have that file at all but my shares work perfectly, have you tried accessing the shares since using the commands?

---

### Post by Ailandar on 2007-12-27
Ok, when I try connect in the graphical mode, host asks the login/password of access. In text mode output is next:

> smbclient -L //localhost/Files #or //127.0.0.1/Files or //192.168.0.1/Files or //kubuntu/Files or 
Password:
Domain=[KUBUNTU] OS=[Unix] Server=[Samba 3.0.26a]
tree connect failed: NT_STATUS_ACCESS_DENIED

For smbclient -L //localhost -N command output is:
> Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.26a]
tree connect failed: NT_STATUS_LOGON_FAILURE

---

### Post by zero-9376 on 2007-12-27
sorry i dont have any experience with samba shares via command line i always use nautilus for accessing the shares. Were you able to connect using nautilus or dolphin as i see your using kubuntu

---

