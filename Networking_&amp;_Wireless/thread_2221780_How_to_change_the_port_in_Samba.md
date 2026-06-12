---
title: "How to change the port in Samba?"
date: 2014-05-03
forum: Networking &amp; Wireless
---

### Post by Nick_Dyer on 2014-05-03
Hi,

I am trying to set my Samba port to my own custom port, but I cannot find it anywhere. I've been looking in smb.conf but I can't find a port configuration. Am I looking in the wrong place?

[RIGHT]-Nick Dyer                    
[/RIGHT]

---

### Post by SeijiSensei on 2014-05-03
You can specify a port for smbd at the [command prompt]("http://www.samba.org/samba/docs/man/manpages-3/smbd.8.html") with -p.  There are also directives to specify ports in [smb.conf]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html"), like "dgram port".

Clients might pose a more difficult problem, especially Windows clients.  The Linux program smbclient lets you specify a port, but that's more like an FTP client than a mounted file share.  In general SMB clients are going to use the ports  set aside officially for Netbios and CIFS.  From /etc/services, they are:
```

netbios-ns      137/tcp                         # NETBIOS Name Service
netbios-ns      137/udp
netbios-dgm     138/tcp                         # NETBIOS Datagram Service
netbios-dgm     138/udp
netbios-ssn     139/tcp                         # NETBIOS session service
netbios-ssn     139/udp
microsoft-ds    445/tcp                         # Microsoft Naked CIFS
microsoft-ds    445/udp

```
SMB is a file-sharing service that should only be used on local-area networks.  If you want to use a different port because you want  expose SMB services on the Internet with a dash of "security via obscurity," my advice would be don't. Use a more secure protocol like sshfs.

---

