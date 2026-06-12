---
title: "I messed up &quot;Shared folders&quot; + How to set up sharing"
date: 2005-10-16
forum: Networking &amp; Wireless
---

### Post by kwaanens on 2005-10-16
Hi!

I'm trying to use NFS or Samba on my home network. (1 laptop that uses Breezy, FC4 and XP, and 1 desktop file server using Breezy)
The problem is on the desktop computer. I have fiddled with "shared folders" from System > Administration so much that now, when I try to open it, it loads (cursor shows as "work in progress") for many seconds, then all buttons are blanked, and the list is empty, hence I can't do anything.
How do I reset everything related to this? Tried completely removing all Samba-related and NFS-related completely, and then installing it over, but that did nothing.

Thanks in advance!

- Ketil

---

### Post by Ovulus on 2005-10-16
I'm having exactly the same problem.
'Shared Folder settings' comes up blank and I can't access the sharing options for any of my folders through the context menus.

I'm trying to set up NFS shares so that I can access my Ubuntu folders from my Macintosh on the same local network, but while the mac sees the Ubuntu server, it never connects.

---

### Post by kwaanens on 2005-10-22
Still no response. Maybe this will help you help us:
When running
```
gskudo shares-admin
```
I get the following:
> (shares-admin:12821): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
- using device duplex
- using device duplex
Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.
*** glibc detected *** double free or corruption (fasttop): 0x08289638 ***


Please help!

- Ketil

---

### Post by p88l on 2005-11-21
Exactly the same problem here...
Any solutions?

Also: 

 *** glibc detected *** double free or corruption (fasttop): 0x08289638 ***

---

### Post by EcliptuX on 2005-11-23
I have the same problem too :(
```
root@ecliptux:/home/ecliptux# shares-admin

(shares-admin:13343): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
*** glibc detected *** double free or corruption (fasttop): 0x0824fef8 ***
```

What's wrong ? :confused:

---

### Post by Eleaf on 2005-11-23
I have the exact same problem as well!!  I cannot get my nfs server up!!!!!!!

---

### Post by Eleaf on 2005-11-23
Somebody, Please help!  It seems like a lot of people have this problem.  There is obviously something wrong.  Setting up a nfs folder is extremely, extremely, extremely hard if this keeps happening!!!!!!!

:confused:

---

### Post by kwaanens on 2005-11-23
I posted a bug for this in [bugzilla.ubuntu.com]("http://bugzilla.ubuntu.com/show_bug.cgi?id=20008").  Feel free to add comments!

- Ketil

---

### Post by Eleaf on 2005-11-23
Cool!  Thank you! =-D

---

### Post by EcliptuX on 2005-11-24
Waiting the bug correction, you can setup your nfs share by editing the file /etc/exports ;)

---

### Post by tjabri on 2005-11-27
Having the same problem here. Console reports error as follows when launching "sudo shares-admin":

*** glibc detected *** double free or corruption (fasttop): 0x082634e8 ***

Added my comments to bug 20008.

---

### Post by melchior on 2006-03-04
hmmmm, i have the dapper dev release and am experiencing this problem... very irritating!

i followed all the nfs server how to's. none seemed to work... i have a samba share to my home directory, but i can't figure out how to create any more shares! 

looking in /etc/samba/smb.conf doesn't explain how to create regular shares?

---

### Post by cabber on 2006-03-17
Did you guys ever get this resolved?  I am having the same issue.  My "Shared Folders" via administration (GUI) is greyed out.  It was working fine10 minutes ago.

---

### Post by kwaanens on 2006-03-18
Nope, there is little response on launchpad to this bug. Hopefully it will be fixed in Dapper.

- Ketil

---

### Post by General Moskovich on 2006-03-20
I have the same problem, too. Anybody found a solution?

---

### Post by tomski on 2006-03-21
any more room left in this boat i have a similar problem
still no answer

---

### Post by efflux on 2006-03-22
Unfortunately I have nothing to add here except to say that I too have this problem.

---

