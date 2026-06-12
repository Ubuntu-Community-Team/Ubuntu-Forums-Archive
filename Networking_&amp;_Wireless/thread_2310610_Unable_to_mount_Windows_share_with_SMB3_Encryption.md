---
title: "Unable to mount Windows share with SMB3 Encryption using mount.cifs"
date: 2016-01-20
forum: Networking &amp; Wireless
---

### Post by email3 on 2016-01-20
I have been scouring google for a few days now trying to solve this issue and have been unable to... maybe my google-fu is lackluster.. I will articulate the best I can what the goal and problems are.

Goal: Mount a Windows 2012R2 SMB3 share with forced "in-transit" encryption.  (also tested with Win 2008R2 and Win 2012)

Server(2012r2) Info:[INDENT]IP: 192.168.220.131
Share "Storage" with default config with two changes:[/INDENT]

[LIST]
[*=1]Set-SmbServerConfiguration -EncryptData $True
[*=1]Set-SmbServerConfiguration -RejectUnencryptedAccess $True
[/LIST]

Tested Client Info (both clients responded the same):[INDENT]Ubuntu 14.04.3LTS with cifs-utils (mount.cifs v6.0)
Ubuntu 15.10 with cifs-utils (mount.cifs b=v6.4)[/INDENT]


The situation:
When I attempt the following command to mount the shared folder:
```
mount -t cifs //192.168.220.131/Storage -o username=bob,vers=3.0 /mnt/storage
``` 
I get the following errors:
```
**Client Error**: *mount error(13): Permission Denied*.
 [B]
Server Error[/B]: *The server received an unencrypted message from client when encryption was required. Message was rejected. * 
```

When change the Windows server setting to *RejectUnencryptedAccess = False*, it connects fine.

Additionally, with *RejectUnencryptedAccess = True* I am able to connect with smbclient just fine with the following:

```
smbclient //192.168.220.131/Storage --user=bob -mSMB3
```

So I know the capability exists to make the connection, but I just can't mount it for filesystem-like access.  It appears that I am having troubles with mount.cifs and SMB3 encrypted session.  I checked out [https://wiki.samba.org/index.php/SMB3_kernel_status](https://wiki.samba.org/index.php/SMB3_kernel_status) and it appears "secure negotiation" and "Encryption and improved packet signing" has been complete.  I see that "share level encryption" is on the "To Do", but I my server configurations are implemented on the session, not share level.

Thank you for your time and consideration.

---

### Post by email3 on 2016-01-21
Is the networking & wireless the appropriate sub-forum to post in?  It seemed the best fit.

---

### Post by bab1 on 2016-01-21
> **email3 said:**
> Is the networking & wireless the appropriate sub-forum to post in?  It seemed the best fit.
The intended use was for TCP/IP connectivity, but folks take the more common view that networking includes server file sharing too.  If you click on the "Report Post" at the lower left of the thread you can tell the mods that you want to move this to the server section.

---

### Post by ajft on 2016-03-07
I'm in the same boat, only with a Samba server that makes an share with mandatory encryption available.  A client Ubuntu 14.04 LTS system can access it via smbclient (Version 4.1.6-Ubuntu) but not with mount.cifs (version: 6.0).  As far as I can tell the "mount.cifs" utility lags behind the rest of the Samba stack and does not implement SMB3 encryption.

---

### Post by SeijiSensei on 2016-03-08
[s]Since smbclient works, maybe you can mount the shares with the smbmount utility that comes with Samba.  If so, you could include the smbmount commands in /etc/rc.local rather than using /etc/fstab.[/s]

Hmm.  Seems the smbmount command is [no longer distributed  by Ubuntu]("https://bugs.launchpad.net/ubuntu/+source/cifs-utils/+bug/1095294").  The current source code at samba.org doesn't include it either.

---

