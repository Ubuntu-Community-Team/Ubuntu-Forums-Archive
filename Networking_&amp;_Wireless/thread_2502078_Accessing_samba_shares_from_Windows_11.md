---
title: "Accessing samba shares from Windows 11"
date: 2024-11-01
forum: Networking &amp; Wireless
---

### Post by mowieco on 2024-11-01
Hello everyone,

I am having issues with accessing samba shares on ubuntu on a windows 11 machine. After installing wsdd I can at least see the ubuntu machine in the windows 11 network folder but it cannot be accessed:

Windows 11 client: folder is not accessible. You might not have the permission…

Ubuntu Server: /etc/log.windows11machinename

```
[2024/11/01 10:47:49.565495,  3] source3/smbd/smb2_server.c:4031(smbd_smb2_request_error_ex)
  smbd_smb2_request_error_ex: smbd_smb2_request_error_ex: idx[1] status[NT_STATUS_PIPE_DISCONNECTED] || at source3/smbd/smb2_read.c:135
[2024/11/01 10:47:49.682645,  3] source3/smbd/smb2_server.c:4031(smbd_smb2_request_error_ex)
  smbd_smb2_request_error_ex: smbd_smb2_request_error_ex: idx[1] status[NT_STATUS_PIPE_DISCONNECTED] || at source3/smbd/smb2_read.c:135
[2024/11/01 10:47:49.802104,  3] source3/smbd/smb2_server.c:4031(smbd_smb2_request_error_ex)
  smbd_smb2_request_error_ex: smbd_smb2_request_error_ex: idx[1] status[NT_STATUS_PIPE_DISCONNECTED] || at source3/smbd/smb2_read.c:135
[2024/11/01 10:47:49.920111,  3] source3/smbd/smb2_server.c:4031(smbd_smb2_request_error_ex)
  smbd_smb2_request_error_ex: smbd_smb2_request_error_ex: idx[1] status[NT_STATUS_PIPE_DISCONNECTED] || at source3/smbd/smb2_read.c:135
[2024/11/01 10:48:00.165784,  3] source3/smbd/server_exit.c:229(exit_server_common)
  Server exit (NT_STATUS_CONNECTION_RESET)
```

The strange thing is, that I can still access the server through the mapped network drives I configured before upgrading the client to windows 11.
Also connecting to the server via //<server>/<folder> does not work.

Any ideals what is wrong with my setup?

```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 24.04.1 LTS
Release:        24.04
Codename:       noble

Samba version 4.19.5-Ubuntu

samba-ad-provision/noble,now 2:4.19.5+dfsg-4ubuntu9 all  [Installiert,automatisch]
samba-common-bin/noble,now 2:4.19.5+dfsg-4ubuntu9 amd64  [Installiert,automatisch]
samba-common/noble,now 2:4.19.5+dfsg-4ubuntu9 all  [Installiert,automatisch]
samba-dsdb-modules/noble,now 2:4.19.5+dfsg-4ubuntu9 amd64  [Installiert,automatisch]
samba-libs/noble,now 2:4.19.5+dfsg-4ubuntu9 amd64  [Installiert,automatisch]
samba-vfs-modules/noble,now 2:4.19.5+dfsg-4ubuntu9 amd64  [Installiert,automatisch]
samba/noble,now 2:4.19.5+dfsg-4ubuntu9 amd64  [installiert]
```

---

### Post by mowieco on 2024-11-01
this is the smbstatus when trying to access via the network folder:

[INDENT]```
Samba version 4.19.5-Ubuntu
PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing
----------------------------------------------------------------------------------------------------------------------------------------
4500    me       me       192.168.0.33 (ipv4:192.168.0.33:4614)     SMB3_11           -                    partial(AES-128-GMAC)


Service      pid     Machine       Connected at                     Encryption   Signing
---------------------------------------------------------------------------------------------
IPC$         4500    192.168.0.33  Fr Nov  1 11:12:27 2024 CET      -            -

```[/INDENT]

And here when accessing the mapped network drives:

[INDENT]```
Samba version 4.19.5-Ubuntu
PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing
----------------------------------------------------------------------------------------------------------------------------------------
4285    me       me       192.168.0.33 (ipv4:192.168.0.33:4634)     SMB3_11           -                    partial(AES-128-GMAC)


Service      pid     Machine       Connected at                     Encryption   Signing
---------------------------------------------------------------------------------------------
me       4285    192.168.0.33  Fr Nov  1 11:16:20 2024 CET      -            -
```[/INDENT]

---

### Post by mowieco on 2024-11-02
Okay.. i tried changing the min max protocol levels (everything _but_ SMB1) - no luck.

Even connecting from another linux client fails:

```
smbclient -L <server>.local --user <user>
Password for [WORKGROUP\<user>]:


        Sharename       Type      Comment
        ---------       ----      -------
cli_rpc_pipe_open_noauth: rpc_pipe_bind for pipe srvsvc failed with error NT_STATUS_CONNECTION_DISCONNECTED
SMB1 disabled -- no workgroup available
```

A different error message but the same result..

Heres whats going on on the server:

```
[2024/11/02 13:19:25.576786,  3] lib/util/access.c:372(allow_access)  Allowed connection from 192.168.0.56 (192.168.0.56)
[2024/11/02 13:19:25.576834,  3] source3/smbd/smb2_service.c:584(make_connection_snum)
  make_connection_snum: Connect path is '/tmp' for service [IPC$]
[2024/11/02 13:19:25.576855,  3] source3/smbd/vfs.c:115(vfs_init_default)
  Initialising default vfs hooks
[2024/11/02 13:19:25.576865,  3] source3/smbd/vfs.c:141(vfs_init_custom)
  Initialising custom vfs hooks from [/[Default VFS]/]
[2024/11/02 13:19:25.681036,  3] source3/smbd/smb2_server.c:4031(smbd_smb2_request_error_ex)
  smbd_smb2_request_error_ex: smbd_smb2_request_error_ex: idx[1] status[NT_STATUS_CONNECTION_DISCONNECTED] || at source3/smbd/smb2_ioctl.c:353
[2024/11/02 13:19:25.794415,  3] source3/smbd/server_exit.c:229(exit_server_common)
  Server exit (NT_STATUS_END_OF_FILE)
[2024/11/02 13:19:53.076808,  3] lib/util/access.c:372(allow_access)
  Allowed connection from 192.168.0.56 (192.168.0.56)
[2024/11/02 13:19:53.076855,  3] source3/smbd/smb2_service.c:584(make_connection_snum)
  make_connection_snum: Connect path is '/tmp' for service [IPC$]
[2024/11/02 13:19:53.076876,  3] source3/smbd/vfs.c:115(vfs_init_default)
  Initialising default vfs hooks
[2024/11/02 13:19:53.076886,  3] source3/smbd/vfs.c:141(vfs_init_custom)
  Initialising custom vfs hooks from [/[Default VFS]/]
[2024/11/02 13:19:53.180751,  3] source3/smbd/smb2_server.c:4031(smbd_smb2_request_error_ex)
  smbd_smb2_request_error_ex: smbd_smb2_request_error_ex: idx[1] status[NT_STATUS_CONNECTION_DISCONNECTED] || at source3/smbd/smb2_ioctl.c:353
[2024/11/02 13:19:53.189362,  3] source3/smbd/server_exit.c:229(exit_server_common)
  Server exit (NT_STATUS_END_OF_FILE)



```

---

### Post by mowieco on 2024-11-02
[B]Workaround:
[/B]
So.. Ubuntu's *AppArmor* seems to be part of the problem. Putting all samba related apps into complaint mode solves the issue:

&#8203;```
sudo aa-complain /usr/bin/smbd
sudo aa-complain samba-dcerpcd samba-bgqd samba-rpcd samba-rpcd-classic samba-rpcd-spoolss
```

But i believe this workaround causes a security risk and i would assume that accessing samba shares from windows and linux should work out of the box without disabling such features?!?

---

