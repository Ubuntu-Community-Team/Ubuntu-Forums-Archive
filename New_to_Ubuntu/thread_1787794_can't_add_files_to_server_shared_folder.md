---
title: "can't add files to server shared folder"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by sjreg1 on 2011-06-21
I've set up an xubuntu server.  I can see the folder through the network but I can't add anything to the folder (get the message 'you need permission to perform this action) from the windows 7 laptop I'm on and I can't add anything directly the folder from the xubuntu system (i.e. copy-paste in the shared folder).  I've added my laptop username to the list of permitted users and the folder is read and write permissable.  How do I add stuff to the share folder?  Any help is appreciated.

---

### Post by jtarin on 2011-06-21
Is this with Samba?

---

### Post by sjreg1 on 2011-06-21
Yes this is with samba.

---

### Post by jtarin on 2011-06-21
> **sjreg1 said:**
> Yes this is with samba.[A few things to remember about Linux Samba shares.]("http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html")

---

### Post by Morbius1 on 2011-06-21
Why not post the output of the following command so we can see how you are set up and what you are sharing:
```
testparm -s
```

---

### Post by crispy_420 on 2011-06-21
As jtarin suggested with his post, look at the share in Xubuntu for its permissions which might need to be opened up a bit then look at the samba permissions. If you can't write to it in Xubuntu, samba can not either.

---

### Post by sjreg1 on 2011-06-21
But I can add files to other folders.  I just moved data from an external to the xubuntu system with no problem.  Additionally, I've been modifying samba files without restriction.  Anyways, the output for testparm -s is below.

mycomputer@mycomputer-desktop:~/Desktop$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[print$]"
Processing section "[printers]"
Processing section "[MyFiles]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    netbios name = MYCOMPUTER
    server string = 
    null passwords = Yes
    username map = /etc/samba/smbusers
    syslog only = Yes
    announce version = 5.0
    name resolve order = hosts wins bcast
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = CUPS

[print$]
    path = /var/lib/samba/printers
    write list = root
    create mask = 0664
    directory mask = 0775
    guest ok = Yes

[printers]
    path = /tmp
    guest ok = Yes
    printable = Yes
    browseable = No
    browsable = No

[MyFiles]
    path = /home/samba/
    force user = mycomputer
    force group = mycomputer
    read only = No
    create mask = 0644

---

### Post by Morbius1 on 2011-06-21
SO the whole share rests on:

Who is "mycomputer"?

Why are you forcing the remote user to be converted to "mycomputer" ?

And does "mycomputer" have write access to /home/samba?

[COLOR=Blue]**EDIT: Figured it out "mycomputer" is you !**[/COLOR]

If you don't feel like answering any of those questions you can start by opening up the permissions on the target folder:

```
sudo chmod 777 /home/samba
```If you had something more sophisticated in mind let us know.

---

### Post by Morbius1 on 2011-06-21
.

---

### Post by sjreg1 on 2011-06-21
YES!!!

IT WORKS!!!

AND I CAN ADD STUFF FROM MY WINDOWS MACHINE!!!

Thank you, Morbius.

---

