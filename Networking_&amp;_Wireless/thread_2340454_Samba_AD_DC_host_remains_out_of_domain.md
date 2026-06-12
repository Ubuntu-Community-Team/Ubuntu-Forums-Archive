---
title: "Samba AD DC host remains out of domain?"
date: 2016-10-18
forum: Networking &amp; Wireless
---

### Post by jeffwji on 2016-10-18
Hi, guys.

I recently setup a Samba-ad-dc server, smb.conf file is:

```
[global]
        workgroup = [COLOR=#ff0000]MYDOMAIN[/COLOR]
        realm = [COLOR=#FF0000]MYDOMAIN[/COLOR][COLOR=#ff0000].LOCAL[/COLOR]
        netbios name = [COLOR=#ff0000]DC[/COLOR]
        server role = active directory domain controller
        server services = s3fs, rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbindd, ntp_signd, kcc, dnsupdate
        idmap_ldb:use rfc2307 = yes


        allow dns updates = nonsecure and secure
        dns forwarder = 172.16.0.1


        # Thanks to Lars for this fix, it stops the syslog
        # being spammed by the lack of a CUPS server.
        printing = CUPS
        printcap name = /dev/null


        log file = /var/log/samba/%m.log
        log level = 1


[netlogon]
        path = /var/lib/samba/sysvol/devops.local/scripts
        read only = No


[sysvol]
        path = /var/lib/samba/sysvol
        read only = No

```

This configuration works fine, I'm able to join new machine and user into this domain, but if I execute smbclient command on this DC, it returns:
> # smbclient -L dc.mydomain.local -U administrator
Enter administrator's password:
Domain=[MYDOMAIN] OS=[Windows 6.1] Server=[Samba 4.3.11-Ubuntu]


        Sharename       Type      Comment
        ---------       ----      -------
        netlogon        Disk
        sysvol          Disk
        IPC$            IPC       IPC Service (Samba 4.3.11-Ubuntu)
Domain=[MYDOMAIN] OS=[Windows 6.1] Server=[Samba 4.3.11-Ubuntu]


        Server               Comment
        ---------            -------


        Workgroup            Master
        ---------            -------
        [COLOR=#ff0000]WORKGROUP[/COLOR]            DC





As you can see DC remains itself out of "MYDOMAIN". I'm not sure is it a problem? And how to fix it?

---

