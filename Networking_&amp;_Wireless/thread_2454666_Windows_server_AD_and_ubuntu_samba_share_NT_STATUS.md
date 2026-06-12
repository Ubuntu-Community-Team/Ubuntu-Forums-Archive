---
title: "Windows server AD and ubuntu samba share: NT_STATUS_ACCESS_DENIED"
date: 2020-12-03
forum: Networking &amp; Wireless
---

### Post by geronimo350 on 2020-12-03
Hi,

I'm trying to share folder from Ubuntu computer (which is joined to AD on windows server 2016) with samba share to devices which are outside of domain. For this purpose I don't care (but would prefer that it's with AD user) if device outside of domain would use guest, local (on samba server) or AD user.

Windows server 2016 machine:[INDENT]
servers as AD, DC, DNS. NTLM is disabled, but since SSSD isn't using it, this is ok.[/INDENT]

Ubuntu computer (samba share):[INDENT]joined within AD domain and servs as media share server. Samba 4.7.6. + SSSD[/INDENT]

Small visualization of setup:
[ATTACH=CONFIG]287506[/ATTACH]

Things I tried:

[LIST]
[*]Allow public guest access in AD
[*]Using local user on samba server
[*]Using AD user
[*]Enable NTLM
[/LIST]

sssd conf:
```

**&#8203;**[sssd]services = nss, pam
config_file_version = 2
domains = home.local
default_domain_suffix = home.local


[domain/home.local]
id_provider = ad
access_provider = ad
auth_provider = ad
ad_gpo_access_control = permissive
krb5_realm = HOME.LOCAL


default_shell = /bin/bash
override_shell = /bin/bash


override_homedir = /home/%d/%u
ad_domain = home.local
realmd_tags = manages-system joined-with-adcli
cache_credentials = True
krb5_store_password_if_offline = True
ldap_id_mapping = True
use_fully_qualified_names = True
fallback_homedir = /home/%u@%d

```

krb5 conf:
```

[libdefaults]
        default_realm = HOME.LOCAL
        kdc_timesync = 1
        ccache_type = 4
        forwardable = true
        proxiable = true


ticket_lifetime = 24h #
renew_lifetime = 7d


fcc-mit-ticketflags = true


[realms]
        ATHENA.MIT.EDU = {
                kdc = kerberos.mit.edu
                kdc = kerberos-1.mit.edu
                kdc = kerberos-2.mit.edu:88
                admin_server = kerberos.mit.edu
                default_domain = mit.edu
        }
        ZONE.MIT.EDU = {
                kdc = casio.mit.edu
                kdc = seiko.mit.edu
                admin_server = casio.mit.edu
        }
        CSAIL.MIT.EDU = {
                admin_server = kerberos.csail.mit.edu
                default_domain = csail.mit.edu
        }
        IHTFP.ORG = {
                kdc = kerberos.ihtfp.org
                admin_server = kerberos.ihtfp.org
        }
        1TS.ORG = {
                kdc = kerberos.1ts.org
                admin_server = kerberos.1ts.org
        }
        ANDREW.CMU.EDU = {
                admin_server = kerberos.andrew.cmu.edu
                default_domain = andrew.cmu.edu
        }
        CS.CMU.EDU = {
                kdc = kerberos-1.srv.cs.cmu.edu
                kdc = kerberos-2.srv.cs.cmu.edu
                kdc = kerberos-3.srv.cs.cmu.edu
                admin_server = kerberos.cs.cmu.edu
        }
        DEMENTIA.ORG = {
                kdc = kerberos.dementix.org
                kdc = kerberos2.dementix.org
                admin_server = kerberos.dementix.org
        }
        stanford.edu = {
                kdc = krb5auth1.stanford.edu
                kdc = krb5auth2.stanford.edu
                kdc = krb5auth3.stanford.edu
                master_kdc = krb5auth1.stanford.edu
                admin_server = krb5-admin.stanford.edu
                default_domain = stanford.edu
        }
        UTORONTO.CA = {
                kdc = kerberos1.utoronto.ca
                kdc = kerberos2.utoronto.ca
                kdc = kerberos3.utoronto.ca
                admin_server = kerberos1.utoronto.ca
                default_domain = utoronto.ca
        }
        HOME.LOCAL = {
                admin_server = ad1.home.local
                default_domain = HOME.LOCAL
        }


[domain_realm]
        .mit.edu = ATHENA.MIT.EDU
        mit.edu = ATHENA.MIT.EDU
        .media.mit.edu = MEDIA-LAB.MIT.EDU
        media.mit.edu = MEDIA-LAB.MIT.EDU
        .csail.mit.edu = CSAIL.MIT.EDU
        csail.mit.edu = CSAIL.MIT.EDU
        .whoi.edu = ATHENA.MIT.EDU
        whoi.edu = ATHENA.MIT.EDU
        .stanford.edu = stanford.edu
        .slac.stanford.edu = SLAC.STANFORD.EDU
        .toronto.edu = UTORONTO.CA
        .utoronto.ca = UTORONTO.CA

```

smb.conf
```

[global]
        client NTLMv2 auth = No
        client schannel = No
        client signing = if_required
        dns proxy = No
        guest account = someUser
        idmap gid = 20000-42000
        idmap uid = 20000-42000
        kerberos method = secrets and keytab
        log file = /var/log/samba/log.%m
        map to guest = Bad User
        max log size = 1000
        ntlm auth = disabled
        obey pam restrictions = Yes
        pam password change = Yes
        panic action = /usr/share/samba/panic-action %d
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        passwd program = /usr/bin/passwd %u
        realm = HOME.LOCAL
        security = ADS
        server role = standalone server
        server signing = if_required
        server string = %h server (Samba, Ubuntu)
        syslog = 0
        unix password sync = Yes
        usershare allow guests = Yes
        workgroup = HOME
        idmap config * : range = 20000-42000
        idmap config * : backend = tdb
        guest ok = Yes
        map acl inherit = Yes
        store dos attributes = Yes[INDENT][printers]
        browseable = No
        comment = All Printers
        create mask = 0700
        path = /var/spool/samba
        printable = Yes




[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers




[multimedia]
        admin users = @MultimediaAdmins@HOME.LOCAL
        create mask = 0755
        directory mask = 0775
        force create mode = 01050
        force directory mode = 01000
        force group = MultimediaUsers
        path = /media/multimedia
        read only = No
        valid users = @MultimediaUsers@HOME.LOCAL




[movies-public]
        comment = Movies public share
        force user = someUser
        guest only = Yes
        path = /media/multimedia/testshare
        valid users = someUser

[/INDENT]

```

Issue that I get when using local user someUser (same as when using AD users) from device otuside of the domain (samba log):
```

[2020/12/03 18:23:05.400262,  0] ../source3/auth/auth_domain.c:122(connect_to_domain_password_server)
  connect_to_domain_password_server: unable to open the domain client session to machine AD1.HOME.LOCAL. Error was : NT_STATUS_ACCESS_DENIED.
[2020/12/03 18:23:05.400363,  0] ../source3/auth/auth_domain.c:185(domain_client_validate)
  domain_client_validate: Domain password server not available.
[2020/12/03 18:23:05.400384,  2] ../source3/auth/auth.c:332(auth_check_ntlm_password)
  check_ntlm_password:  Authentication for user [someUser] -> [someUser] FAILED with error NT_STATUS_NO_LOGON_SERVERS, authoritative=1
[2020/12/03 18:23:05.400400,  2] ../auth/auth_log.c:760(log_authentication_event_human_readable)
  Auth: [SMB2,(null)] user []\[someUser] at [&#269;et, 03 pro 2020 18:23:05.400392 CET] with [NTLMv2] status [NT_STATUS_NO_LOGON_SERVERS] workstation [] remote host [ipv4:10.1.1.13:39456] mapped to []\[someUser]. local host [ipv4:10.1.2.7:445]
[2020/12/03 18:23:05.400465,  2] ../auth/auth_log.c:220(log_json)
  JSON Authentication: {"timestamp": "2020-12-03T18:23:05.400423+0100", "type": "Authentication", "Authentication": {"version": {"major": 1, "minor": 0}, "status": "NT_STATUS_NO_LOGON_SERVERS", "localAddress": "ipv4:10.1.2.7:445", "remoteAddress": "ipv4:10.1.1.13:39456", "serviceDescription": "SMB2", "authDescription": null, "clientDomain": "", "clientAccount": "someUser", "workstation": "", "becameAccount": null, "becameDomain": null, "becameSid": "(NULL SID)", "mappedAccount": "someUser", "mappedDomain": "", "netlogonComputer": null, "netlogonTrustAccount": null, "netlogonNegotiateFlags": "0x00000000", "netlogonSecureChannelType": 0, "netlogonTrustAccountSid": "(NULL SID)", "passwordType": "NTLMv2"}}
[2020/12/03 18:23:05.400480,  2] ../auth/gensec/spnego.c:605(gensec_spnego_server_negTokenTarg)
  SPNEGO login failed: NT_STATUS_NO_LOGON_SERVERS

```

Everything works for devices that are joined within AD, but is there a way to setup access (guest or with some type of authentication) for devices that are not joined in AD domain ?

---

