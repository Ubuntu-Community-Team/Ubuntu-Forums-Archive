---
title: "Need Samba AD member join help"
date: 2016-07-31
forum: Networking &amp; Wireless
---

### Post by shashchatter on 2016-07-31
Hi,

I have setup a Samba AD Domain Controller (Ubuntu 16.04 LTS), and at face value it looks to be working.  The server config and steps I went through are here: [http://pastebin.com/hnfZdn7i](http://pastebin.com/hnfZdn7i)

The only thing unusual is I had to add Kerberos principals manually for "administrator" and "admin/admin".

On the client/AD Member side (client config here: [http://pastebin.com/sbPZUAEQ](http://pastebin.com/sbPZUAEQ)), which is also Ubuntu 16.04 LTS, I can kinit and receive principals correctly.  However, the "net ads join" fails, as below.  I also tried joining a Mac to the domain, and the error I get mentions "make sure both server and client are setup for the same NTP servers" or something like that, which I have ensured that all three machines are syncing of the Ubuntu NTP servers (including the Mac).

When I used to use Unix auth with Samba, I used to have to add "machine$" using "useradd -m".  I wonder if I need to do something similar with Kerberos as well? I tied adding with "samba-tool", it didn't help.  I tried adding prinicpals to kKerberos, but it didn't help, and I am not sure what the exact format of the principal would be any way.

Any and all help would be most appreciated!

Thanks,
Shash

Here's the client failure log:

chatterjees@ChatterBuntu:~$ sudo net ads join -S chattersrv.home.thechatterjees.net -U Administrator -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
Registered MSG_REQ_POOL_USAGE
Registered MSG_REQ_DMALLOC_MARK and LOG_CHANGED
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
added interface enp2s0 ip=192.168.1.13 bcast=192.168.1.255 netmask=255.255.255.0
Enter Administrator's password:
libnet_Join:
    libnet_JoinCtx: struct libnet_JoinCtx
        in: struct libnet_JoinCtx
            dc_name                  : 'chattersrv.home.thechatterjees.net'
            machine_name             : 'CHATTERBUNTU'
            domain_name              : *
                domain_name              : 'HOME.THECHATTERJEES.NET'
            domain_name_type         : JoinDomNameTypeDNS (1)
            account_ou               : NULL
            admin_account            : 'Administrator'
            admin_domain             : NULL
            machine_password         : NULL
            join_flags               : 0x00000023 (35)
                   0: WKSSVC_JOIN_FLAGS_IGNORE_UNSUPPORTED_FLAGS
                   0: WKSSVC_JOIN_FLAGS_JOIN_WITH_NEW_NAME
                   0: WKSSVC_JOIN_FLAGS_JOIN_DC_ACCOUNT
                   0: WKSSVC_JOIN_FLAGS_DEFER_SPN
                   0: WKSSVC_JOIN_FLAGS_MACHINE_PWD_PASSED
                   0: WKSSVC_JOIN_FLAGS_JOIN_UNSECURE
                   1: WKSSVC_JOIN_FLAGS_DOMAIN_JOIN_IF_JOINED
                   0: WKSSVC_JOIN_FLAGS_WIN9X_UPGRADE
                   0: WKSSVC_JOIN_FLAGS_ACCOUNT_DELETE
                   1: WKSSVC_JOIN_FLAGS_ACCOUNT_CREATE
                   1: WKSSVC_JOIN_FLAGS_JOIN_TYPE
            os_version               : NULL
            os_name                  : NULL
            os_servicepack           : NULL
            create_upn               : 0x00 (0)
            upn                      : NULL
            modify_config            : 0x00 (0)
            ads                      : NULL
            debug                    : 0x01 (1)
            use_kerberos             : 0x00 (0)
            secure_channel_type      : SEC_CHAN_WKSTA (2)
Connecting to 192.168.1.11 at port 445
Doing spnego session setup (blob length=96)
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
GENSEC backend 'gssapi_spnego' registered
GENSEC backend 'gssapi_krb5' registered
GENSEC backend 'gssapi_krb5_sasl' registered
GENSEC backend 'spnego' registered
GENSEC backend 'schannel' registered
GENSEC backend 'naclrpc_as_system' registered
GENSEC backend 'sasl-EXTERNAL' registered
GENSEC backend 'ntlmssp' registered
GENSEC backend 'ntlmssp_resume_ccache' registered
GENSEC backend 'http_basic' registered
GENSEC backend 'http_ntlm' registered
GENSEC backend 'krb5' registered
GENSEC backend 'fake_gssapi_krb5' registered
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
get_dc_list: preferred server list: "chattersrv.home.thechatterjees.net, *"
Successfully contacted LDAP server 192.168.1.11
Connected to LDAP server chattersrv.home.thechatterjees.net
ads_sasl_spnego_bind: got OID=1.2.840.48018.1.2.2
ads_sasl_spnego_bind: got OID=1.2.840.113554.1.2.2
ads_sasl_spnego_bind: got OID=1.3.6.1.4.1.311.2.2.10
kerberos_kinit_password [EMAIL="Administrator@HOME.THECHATTERJEES.NET"]Administrator@HOME.THECHATTERJEES.NET[/EMAIL] failed: Client not found in Kerberos database
libnet_Join:
    libnet_JoinCtx: struct libnet_JoinCtx
        out: struct libnet_JoinCtx
            account_name             : NULL
            netbios_domain_name      : 'CHATTERDOMAIN'
            dns_domain_name          : 'home.thechatterjees.net'
            forest_name              : 'home.thechatterjees.net'
            dn                       : NULL
            domain_sid               : *
                domain_sid               : S-1-5-21-148286683-2101334516-1739462661
            modified_config          : 0x00 (0)
            error_string             : 'failed to connect to AD: Client not found in Kerberos database'
            domain_is_ad             : 0x01 (1)
            result                   : WERR_GENERAL_FAILURE
Failed to join domain: failed to connect to AD: Client not found in Kerberos database
return code = -1


Here's the

---

### Post by shashchatter on 2016-07-31
I also tried using "-U administrator" (which is in the Kerberos database), but that didn't work either:

chatterjees@ChatterBuntu:~$ sudo net ads join -S chattersrv.home.thechatterjees.net -U administrator -d3
[sudo] password for chatterjees: 
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
Registered MSG_REQ_POOL_USAGE
Registered MSG_REQ_DMALLOC_MARK and LOG_CHANGED
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[global]"
added interface enp2s0 ip=192.168.1.13 bcast=192.168.1.255 netmask=255.255.255.0
Enter administrator's password:
libnet_Join:
    libnet_JoinCtx: struct libnet_JoinCtx
        in: struct libnet_JoinCtx
            dc_name                  : 'chattersrv.home.thechatterjees.net'
            machine_name             : 'CHATTERBUNTU'
            domain_name              : *
                domain_name              : 'HOME.THECHATTERJEES.NET'
            domain_name_type         : JoinDomNameTypeDNS (1)
            account_ou               : NULL
            admin_account            : 'administrator'
            admin_domain             : NULL
            machine_password         : NULL
            join_flags               : 0x00000023 (35)
                   0: WKSSVC_JOIN_FLAGS_IGNORE_UNSUPPORTED_FLAGS
                   0: WKSSVC_JOIN_FLAGS_JOIN_WITH_NEW_NAME
                   0: WKSSVC_JOIN_FLAGS_JOIN_DC_ACCOUNT
                   0: WKSSVC_JOIN_FLAGS_DEFER_SPN
                   0: WKSSVC_JOIN_FLAGS_MACHINE_PWD_PASSED
                   0: WKSSVC_JOIN_FLAGS_JOIN_UNSECURE
                   1: WKSSVC_JOIN_FLAGS_DOMAIN_JOIN_IF_JOINED
                   0: WKSSVC_JOIN_FLAGS_WIN9X_UPGRADE
                   0: WKSSVC_JOIN_FLAGS_ACCOUNT_DELETE
                   1: WKSSVC_JOIN_FLAGS_ACCOUNT_CREATE
                   1: WKSSVC_JOIN_FLAGS_JOIN_TYPE
            os_version               : NULL
            os_name                  : NULL
            os_servicepack           : NULL
            create_upn               : 0x00 (0)
            upn                      : NULL
            modify_config            : 0x00 (0)
            ads                      : NULL
            debug                    : 0x01 (1)
            use_kerberos             : 0x00 (0)
            secure_channel_type      : SEC_CHAN_WKSTA (2)
resolve_hosts: Attempting host lookup for name chattersrv.home.thechatterjees.net<0x20>
Connecting to 192.168.1.11 at port 445
Doing spnego session setup (blob length=96)
got OID=1.2.840.48018.1.2.2
got OID=1.2.840.113554.1.2.2
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
GENSEC backend 'gssapi_spnego' registered
GENSEC backend 'gssapi_krb5' registered
GENSEC backend 'gssapi_krb5_sasl' registered
GENSEC backend 'spnego' registered
GENSEC backend 'schannel' registered
GENSEC backend 'naclrpc_as_system' registered
GENSEC backend 'sasl-EXTERNAL' registered
GENSEC backend 'ntlmssp' registered
GENSEC backend 'ntlmssp_resume_ccache' registered
GENSEC backend 'http_basic' registered
GENSEC backend 'http_ntlm' registered
GENSEC backend 'krb5' registered
GENSEC backend 'fake_gssapi_krb5' registered
Got challenge flags:
Got NTLMSSP neg_flags=0x62898215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x62088215
get_dc_list: preferred server list: "chattersrv.home.thechatterjees.net, *"
Successfully contacted LDAP server 192.168.1.11
Connected to LDAP server chattersrv.home.thechatterjees.net
ads_sasl_spnego_bind: got OID=1.2.840.48018.1.2.2
ads_sasl_spnego_bind: got OID=1.2.840.113554.1.2.2
ads_sasl_spnego_bind: got OID=1.3.6.1.4.1.311.2.2.10
gss_init_sec_context failed with [ Miscellaneous failure (see text): LOOKING_UP_SERVER]
SPNEGO(gse_krb5) creating NEG_TOKEN_INIT failed: NT_STATUS_INTERNAL_ERROR
kinit succeeded but ads_sasl_spnego_gensec_bind(KRB5) failed: An internal error occurred.
libnet_Join:
    libnet_JoinCtx: struct libnet_JoinCtx
        out: struct libnet_JoinCtx
            account_name             : NULL
            netbios_domain_name      : 'CHATTERDOMAIN'
            dns_domain_name          : 'home.thechatterjees.net'
            forest_name              : 'home.thechatterjees.net'
            dn                       : NULL
            domain_sid               : *
                domain_sid               : S-1-5-21-148286683-2101334516-1739462661
            modified_config          : 0x00 (0)
            error_string             : 'failed to connect to AD: An internal error occurred.'
            domain_is_ad             : 0x01 (1)
            result                   : WERR_GENERAL_FAILURE
Failed to join domain: failed to connect to AD: An internal error occurred.
return code = -1

---

### Post by shashchatter on 2016-08-01
Never mind ... figured it out.  What I was missing was that Samba AD DC includes a built-in KDC, I did not need to setup a separate Kerberos domain server.  So "sudo apt remove --purge krb5-kdc" and a Samba restart is all I needed, and all is well.

---

