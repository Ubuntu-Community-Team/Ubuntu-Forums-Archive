---
title: "Unable to follow symbolic links in a Windows share"
date: 2017-11-21
forum: Networking &amp; Wireless
---

### Post by brian0975 on 2017-11-21
[LIST]
[*]    Ubuntu Desktop 16.04.3 LTS
[*]    Kernel - 4.10.0-40-generic
[*]    cifs-utils - 2:6.4-1ubuntu1.1
[*]    samba & smbclient - 2:4.3.11+dfsg-0ubuntu0.16.04.12
[/LIST]

We are a large company with a Windows Server backend and a mix of Windows, MacOS, CentOS and Ubuntu clients. We use DFS heavily for file share management.

Recently, we've begin disabling SMB v1 on the servers to mitigate its associated vulnerabilities. This has not been any trouble for the Windows or Mac clients, however, the Ubuntu and CentOS clients are having a lot of trouble.

Specifically, mounting a DFS share fails once the client tries to see past the symbolic link that points to the absolute path.

[FONT=courier new]//namespaceserver/share/directory/symboliclink[/FONT] points to [FONT=courier new]//realserver/sharename[/FONT]

This is the command I'm using:

    [FONT=courier new]sudo mount.cifs //namespaceserver/share /mnt/share -o vers=2.1,user='user@domain.com'[/FONT]

The mount is successful and I can navigate within the DFS namespace but, once I try to go past the symbolic link, I get:

    [FONT=courier new]ls: cannot access '/mnt/share/directory/symboliclink': Function not supported.[/FONT]

I've added [FONT=courier new]follow symlinks=yes[/FONT] and [FONT=courier new]unix extensions=no[/FONT] to the smb.conf file but that didn't help.

Any advice would be appreciated as I've spent about ten hours on this issue so far.

---

