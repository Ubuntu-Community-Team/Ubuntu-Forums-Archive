---
title: "kadmin: Missing parameters in krb5.conf required for kadmin client"
date: 2017-02-01
forum: Networking &amp; Wireless
---

### Post by fenggui on 2017-02-01
I am trying to install KDC server on one of our Ubuntu 14.04 trusty servers.

I am following the document titled "Kerberos" ([https://help.ubuntu.com/community/Kerberos](https://help.ubuntu.com/community/Kerberos)).

Here is my /etc/krb5kdc/kdc.conf
-----------------------------------------------------------------------------------------------------
[kdcdefaults]
    kdc_ports = 750,88
    default_realm = GLOBAL.BC.NET


[realms]
    GLOBAL.BC.NET = {
        database_name = /var/lib/krb5kdc/principal
        admin_keytab = FILE:/etc/krb5kdc/kadm5.keytab
        acl_file = /etc/krb5kdc/kadm5.acl
        key_stash_file = /etc/krb5kdc/stash
        kdc_ports = 750,88
        max_life = 10h 0m 0s
        max_renewable_life = 7d 0h 0m 0s
        master_key_type = des3-hmac-sha1
        supported_enctypes = aes256-cts:normal arcfour-hmac:normal des3-hmac-sha1:normal des-cbc-crc:normal des:normal des:v4 des:norealm des:onlyrealm des:afs3
        default_principal_flags = +preauth
    }
-----------------------------------------------------------------------------------------------------

Here is my /etc/krb5kdc/kadm5.acl

-----------------------------------------------------------------------------------------------------
*/admin@GLOBAL.BC.NET     *
-----------------------------------------------------------------------------------------------------


Here is my /etc/krb5.conf
-----------------------------------------------------------------------------------------------------
[libdefaults]
    default_realm = GLOBAL.BC.NET


# The following krb5.conf variables are only for MIT Kerberos.
    krb4_config = /etc/krb.conf
    krb4_realms = /etc/krb.realms
    kdc_timesync = 1
    ccache_type = 4
    forwardable = true
    proxiable = true


[realms]
    GLOGAL.BC.NET = {
        kdc = 10.5.18.103
        admin_server = 10.5.18.103
        default_domain = GLOBAL.BC.NET
    }


[domain_realm]
        .global.bc.net = GLOBAL.BC.NET
        global.bc.net = GLOBAL.BC.NET


[login]
    krb4_convert = true
    krb4_get_tickets = false

-----------------------------------------------------------------------------------------------------

10.5.18.103 is the IP of the KDC server I am trying to configure.

I created the Kerberos database with the 
#krb5_newrealm

I cannot run "sudo kadmin", the error says that
Authenticating as principal root/admin@GLOBAL.BC.NET with password.
kadmin: Missing parameters in krb5.conf required for kadmin client while initializing kadmin interface

However, I could run "kadmin.local" on the server and was able to add principals to the Kerberos database. I also added "root/admin@GLOBAL.BC.NET" to the Kerberos database. But as I run "sudo kadmin", it still gives me same error message.

I am wondering what the missing parameter is in the krb5.conf?

Thanks.

---

### Post by ajgreeny on 2017-02-01
Duplicate of [https://ubuntuforums.org/showthread.php?t=2351253&p=13601844#post13601844](https://ubuntuforums.org/showthread.php?t=2351253&p=13601844#post13601844)

**Please do not create duplicate posts;** it is confusing for all including you and dilutes the forum's ability to help.

---

