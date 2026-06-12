---
title: "Ubuntu 18.04 Connect to Windows Workgroup Problem"
date: 2018-05-03
forum: Networking &amp; Wireless
---

### Post by evansn on 2018-05-03
I've recently installed 18.04 to replace 16.04. Previously I was able to connect to a Windows PC (Windows 8.1) on the network using Samba, but now I am unable to do so.

I have installed Samba, and my smb.conf reads as follows:
[INDENT]#============================ Global definition ================================
 
[global]
workgroup = WORKGROUP
name resolve order = bcast host lmhosts wins
server string = Samba Server %v
netbios name = Ubuntu18
security = user
map to guest = Bad User
dns proxy = no
bind interfaces only = yes

#============================ Share Definitions ============================== 

[Public]
   path = /samba/public
   writable = yes
   guest ok = yes
   guest only = yes
   read only = no
   create mode = 0777
   directory mode = 0777
   force user = nobody
[/INDENT]

I have confirmed that the share is available from Windows (dual-boot laptop - Windows 7 can see and use the share) and it was working earlier this week when I was running  16.04.

I have no Firewall running on Ubuntu.

When I click 'other locations' it shows 'Windows Network', and I can then get to 'HOME' and 'WORKGROUP' However, when I double-click WORKGROUP I get the error:

**Unable to access location. Failed to retrieve share list from the server: Success**

I have a shortcut to the server which was restored with my backup (I think) - it points to smb://[PC_NAME]/c (the shared folder) but when I click on it I get a dialog box asking for a password. It has boxes for Username, Domain and Password, but no matter what combination of information I put in I cannot connect. There is also the option to connect Anonymously, but that doesn't connect either.

Any help much appreciated. Thanks.

---

### Post by LHammonds on 2018-05-03
Look at the [release notes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes#Default_CIFS.2FSMB_protocol_version_change_in_CIFS_mounts) regarding the CIFS version.  See if changing the vers=1.0 fixes your issue.

---

### Post by evansn on 2018-05-09
Thank you for your reply - I was not on the same LAN for a few days so was unable to try your suggestion. In the meantime, however, I had a few other issues with 18.04 so I've rolled back to 16.04 and I can now connect again.

---

### Post by Morbius1 on 2018-05-09
In the release notes you will find this:
> Default CIFS/SMB protocol version change in CIFS mounts

Since 17.10, the default SMB protocol used when mounting remote CIFS filesystems via mount.cifs (from the cifs-utils package) changed to 2.1 or higher, depending on what is negotiated with the server.

If no version is specified when mounting such a remote share, the following will be logged: No dialect specified on mount. Default has changed to a more secure dialect, SMB2.1 or later (e.g. SMB3),
from CIFS (SMB1). To use the less secure SMB1 dialect to access old servers which do not support SMB3
(or SMB2.1) specify vers=1.0 on mount.
The problem with that is that it doesn't go far enough.

The biggest issue with most Ubuntu desktop users will be browsing for shares from their file manager as is the case in this thread. The file manager does not use mount.cifs it uses libsmbclient. That is a completely different mechanism and works independent of the defaults of mount.cifs.

In addition to the cifs defaults contained within the Linux kernel itself there was also a change to the defaults that samba itself made to the samba client. This is where smb dialect negotiation takes place and it is here that the upper limit of that negotiation was also changed from smb1 ( what samba calls NT1 ) to smb3. This was done so that you could connect to a machine where SMB1 was disabled like WIn10, etc ...

In a perfect world it should make no difference where the upper limit is set since ... well ... it is negotiated between server and client to determine the best value. But what happens is that host browsing is disabled resulting in any number of error messages apparently determined by lunar cycles and humidity levels.. 

The only way out of this - at the moment - is to edit /etc/samba/smb.conf ( which by the way does not exist by default in Ubuntu any longer so you will have to install thee **smbclient** package first ) and change it back to the old default:
```
client max protocol = NT1
```
Put it right below the **workgroup = WORKGROUP** line.

---

### Post by tony-whelan2 on 2018-06-03
Thank you Morbius1. 
I was able to browse the other linux machines on the default WORKGROUP but couldn't browse linux machines on my second workgroup
Editing smb.conf as suggested solved the problem for me.

---

