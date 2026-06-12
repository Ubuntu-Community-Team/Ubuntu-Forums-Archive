---
title: "Samba4: Cannot access files and subfolders inside the share"
date: 2015-08-16
forum: Networking &amp; Wireless
---

### Post by Camilo_Lozano_III on 2015-08-16
Hello,

I've been using Ubuntu for a quite a while now. My previous file server is ubuntu 14.0.4 + samba 4.x. The server crash and rebuilding it again but this time i used ubuntu 15.0.4 + samba 4.x

```

root@dc:~# samba -V
Version 4.1.13-Ubuntu
root@dc:~# smbclient -V
Version 4.1.13-Ubuntu

```

here is my smb.cnf

```

root@dc:~# testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[netlogon]"
Processing section "[sysvol]"
Processing section "[jdrive]"
Loaded services file OK.
Server role: ROLE_ACTIVE_DIRECTORY_DC
[global]
        workgroup = ALPHAONE
        realm = ALPHAONE.LOCAL
        server role = active directory domain controller
        passdb backend = samba_dsdb
        dns forwarder = 192.168.0.254
        server services = rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbind, ntp_signd, kcc, dnsupdate, dns, smb
        dcerpc endpoint servers = epmapper, wkssvc, rpcecho, samr, netlogon, lsarpc, spoolss, drsuapi, dssetup, unixinfo, browser, eventlog6, backupkey, dnsserver, winreg, srvsvc
        rpc_server:tcpip = no
        rpc_daemon:spoolssd = embedded
        rpc_server:spoolss = embedded
        rpc_server:winreg = embedded
        rpc_server:ntsvcs = embedded
        rpc_server:eventlog = embedded
        rpc_server:srvsvc = embedded
        rpc_server:svcctl = embedded
        rpc_server:default = external
        idmap_ldb:use rfc2307 = yes
        idmap config * : backend = tdb
        force user = alphagroup
        hosts allow = 127.0.0.1, 127.0.1.1, 192.168.0.0/24
        hosts deny = 0.0.0.0/0
        map archive = No
        map readonly = no
        store dos attributes = Yes
        vfs objects = dfs_samba4, acl_xattr

[netlogon]
        path = /var/lib/samba/sysvol/alphaone.local/scripts
        read only = No

[sysvol]
        path = /var/lib/samba/sysvol
        read only = No

[jdrive]
        comment = AlphaGroup Building Consultants
        path = /jdrive
        read only = No
        create mask = 0755
        guest ok = Yes


```

For me it should not be rocket science, but it seems i cannot resolve it. 

I can see the share in Windows 7, I can see all the files inside the share folder. 

```

root@dc:~# smbclient //alphaone.local/netlogon -Ualphagroup -c 'ls'
Enter alphagroup's password:
Domain=[ALPHAONE] OS=[Unix] Server=[Samba 4.1.13-Ubuntu]
  .                                   D        0  Wed Aug 12 22:09:16 2015
  ..                                  D        0  Wed Aug 12 22:13:53 2015

                50815 blocks of size 0. 27341 blocks available
root@dc:~#
root@dc:~# smbclient //alphaone.local/netlogon -Ualphagroup -c 'ls'
Enter alphagroup's password:
Domain=[ALPHAONE] OS=[Unix] Server=[Samba 4.1.13-Ubuntu]
  .                                   D        0  Wed Aug 12 22:09:16 2015
  ..                                  D        0  Wed Aug 12 22:13:53 2015

                50815 blocks of size 0. 27341 blocks available
root@dc:~# smbclient //alphaone.local/jdrive -Ualphagroup -c 'ls'
Enter alphagroup's password:
Domain=[ALPHAONE] OS=[Unix] Server=[Samba 4.1.13-Ubuntu]
  .                                   D        0  Sat Aug 15 00:31:52 2015
  ..                                  D        0  Thu Aug 13 06:42:42 2015
  Alpha Logos                         D        0  Fri Aug 14 15:23:34 2015
  A77                                 D        0  Tue Jul 21 12:35:15 2015
  AlphaDNS_Setup.exe                  N  2195898  Sat Aug 15 00:31:49 2015
  2015                                D        0  Fri Aug 14 13:40:31 2015
  2014                                D        0  Fri Aug 14 12:21:50 2015


                50815 blocks of size 0. 27341 blocks available
root@dc:~#

```

```

root@dc:/jdrive# ls -lsa
total 127220
    4 drwxrwxrwx  31 nobody nogroup     4096 Aug 15 00:31 .
    4 drwxr-xr-x  25 root   root        4096 Aug 13 06:42 ..
    8 drwxrwxrwx  13 nobody nogroup     4096 Aug 14 12:21 2014
    8 drwxrwxrwx   9 nobody nogroup     4096 Aug 14 13:40 2015
    8 drwxrwxrwx   3 nobody nogroup     4096 Jul 21 12:35 A77
    8 drwxrwxrwx  13 nobody nogroup     4096 Jul  3 09:31 ALPHABC
 2152 -rwxrwxrwx   1 nobody nogroup  2195898 Aug 15 00:31 AlphaDNS_Setup.exe
  676 -rwxrwxrwx   1 nobody nogroup   684366 Aug 15 00:31 AlphaDrive_Setup.exe

```

But if I open the sub-folders of the share folder, it says: Access Denied (both CLI in the fileserver and Windows 7 gives same error)

even opening a file, i got same message.

```

root@dc:~# smbclient //alphaone.local/jdrive -Ualphagroup -c 'ls 2015/*'
Enter alphagroup's password:
Domain=[ALPHAONE] OS=[Unix] Server=[Samba 4.1.13-Ubuntu]
NT_STATUS_ACCESS_DENIED listing \2015\*

```

[IMG]http://www.camilord.com/docs/access_denied_share.png[/IMG]

i am really puzzled of this issue because same config of samba i used, but doesn't work. is there something wrong with ubuntu 15.0.4?

or is there something to do the file system? i used ext4 though but still the same last file server i setup...

anybody can give a solution please? 

please help.. thanks.

---

### Post by bab1 on 2015-08-17
At one time Samba (Samba.org) recommended that you not use a Samba4 AD-DC as a fileserver also.  The reasons given had to do with winbind problems and the integration of smbd/nmbd with the new *samba daemon* (samba).  It appears that lately things might have changed, but you have to be careful with file permissions.  See [**here**]("http://samba.2283325.n4.nabble.com/using-the-DC-as-a-file-Server-in-AD-td4686970.html") for an interesting take on the situation.

---

### Post by Camilo_Lozano_III on 2015-08-17
yeah.  there are a lot issues on ubuntu 15. i reformat my file server again and install ubuntu 14.0.4 and done all the configuration within 5mins. its up and running now and serving files.

anyway, thanks.

---

