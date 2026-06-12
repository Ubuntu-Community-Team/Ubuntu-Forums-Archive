---
title: "Unix permissions problem with Win2k3 Storage Server cifs share"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by rockfx01 on 2008-07-07
I am having some trouble setting user permissions on a Windows 2003 Storage server cifs share from a Linux system.  The behavior is extremely odd and I have not been able to solve the problem thus far.

**The setup is as follows:**

1. There is a Windows 2003 R2 Active Directory server which is used as the domain controller.  Microsoft Identity Management for Unix is installed and several groups/users set up with Unix uid/gids in Active Directory.

2. There is a RHEL 4 server set up.  It authenticates Active Directory users using LDAP and Kerberos per [this article]("http://www.interopsystems.com/LearningCenter/Native_LDAP_native_Kerberos_and_AD_services.htm").

3. There is a Windows 2003 R2 Storage Server set up with Services for NFS installed.  It is set up to use Active Directory lookup for Unix user authentication, although I am not sure this is necessary given the LDAP/Kerberos setup of the RHEL server.

We are not actually using NFS at the moment, however, due to language incompatibility issues we ran into between the RHEL server and W2003R2 NFS implementation.  The storage server is sharing a folder via Samba, and that folder is mounted via cifs on the RHEL system using the Domain Administrator account.  The Redhat system can read/write files just fine.


**The Problem:**

Although I can read write files without any problems, odd issues arise when trying to set user permissions from the RHEL server.

Let's say I create the file "test.txt" on the storage server from the RHEL server.  Then I do a "chown domainuser:domaingroup test.txt".  On the RHEL server, if i perform a "ls -l" command, it will list the file as if it has the correct ownership and permissions (if set with chmod).

If I look at the same file on the storage server itself or from any Windows client, the file will have inherited the rights and ownership of the parent folder.

I.E. if, on the storage server, the parent folder is owned by the local administrator and the local 'Administrator', Domain 'Admin' user and 'Domain Admins' group have full permissions on the folder and then a new file is created and permissions set from the RHEL server, that file will receive the parent folder permissions regardless of the permissions set from the RHEL server.  HOWEVER, if I do an 'ls -l', the file will be listed with the correct Unix permissions even though the unix owner/group doesn't even show up anywhere in the Windows file permissions if I look at the file permissions directly on the storage server.  Keep in mind that the 'Unix' owner and group are actually Active Directory users/groups with Unix attributes, so the Unix uid and gid map back to A.D. users.


The odd thing is I had this setup working last Wednesday, then after someone changed some permissions on the storage server, everything stopped working.  We were at one point using NFS and I don't know if that is related, but permissions are definitely hosed at the moment.  We have tried setting up a separate set of servers the same way to mirror our original setup, but we are having the same permissions problems in the new setup.

Help?

---

### Post by rockfx01 on 2008-07-07
Some more info:

When I enable NFS sharing on the storage server for the share and then mount the share via NFS on the RHEL server, the user permissions work fine.  There seems to be something getting hosed up between Samba on the linux system and on the storage server.

If I mount the share via NFS on RHEL, it displays the user and group ownership of files correctly.  So an 'ls -l' will display:

dwrxwrx--- domainuser domaingroup FolderName

If I turn off NFS and mount the directory via cifs, an 'ls -l' will display:

dwrxwrxwrx root root FolderName

...for all files.  If I perform a chmod or chown on the files it will, as above, 'set' the permissions and I can view the permissions as if they are correct in Linux, but when I look at the files on the storage server, they have not changed at all.

All in all, it appears the Linux server is having a problem translating the user and group (id) ownership of files when the share is mounted via cifs instead of nfs.

Is there a way to authenticate the A.D. user uid and gid information correctly when mounting a cifs share as opposed to nfs?  Is there another pam config file I need to edit or perhaps something different needs to be done in the samba.conf or other configuration settings?

---------------------
One last note:

I am using a modified "/etc/pam.d/samba" file, instead of "/etc/pam.d/system-auth" as suggested in the article linked in my first post.  Samba is then configured to use pam for authentication. This way network users with Unix permissions cannot log in to the RHEL server, but they can gain access to smb shares on the RHEL server if they are in the correct group.

Other than that, everything is set up pretty much exactly as the article describes.


Thanks,
-rockfx01

---

