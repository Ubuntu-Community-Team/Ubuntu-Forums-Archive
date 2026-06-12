---
title: "SAMBA: Multiple Shares Question"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by iXneonXi on 2007-06-29
Hello, I have a share that is password protected in SAMBA. It asks for the password and I give my username and the password I set using smbpasswd. Is it possible (using the same computer) to create a second shared folder that is not password protected while maintaining the passworded share?

---

### Post by ronocdh on 2007-06-29
> **iXneonXi said:**
> Hello, I have a share that is password protected in SAMBA. It asks for the password and I give my username and the password I set using smbpasswd. Is it possible (using the same computer) to create a second shared folder that is not password protected while maintaining the passworded share?
It is probably best to ask such a specific question in the Networking forum.

---

### Post by lintoon on 2007-06-29
Maybe create a public folder within samba.

---

### Post by Gallows on 2007-06-30
To answer the question yes it is possible to set up a password protected share and a openly accessible share  on the same samba server.  Have a look [here]("http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html#id325983") at the explanation of share level security.

---

### Post by iXneonXi on 2007-07-02
> **Gallows said:**
> To answer the question yes it is possible to set up a password protected share and a openly accessible share  on the same samba server.  Have a look [here]("http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/ServerType.html#id325983") at the explanation of share level security.

Here is a snippet from my smb.conf.
Notice the share level security. The issue is that when I use share level security when connecting from a Windows computer, It does not ask a password and simply allows access to the shares (Audi01 being write-protected and Shared being read/write).

```

[global]

 security = share

 [Audi01]
 path = /media/audio/aud
 comment = Audi0
 available = yes
 browsable = yes
 public = yes
 writable = no

 [Shared]
 path = /media/shared
 comment = Shared
 available = yes
 browsable = yes
 public = yes
 writable = yes

```

---

