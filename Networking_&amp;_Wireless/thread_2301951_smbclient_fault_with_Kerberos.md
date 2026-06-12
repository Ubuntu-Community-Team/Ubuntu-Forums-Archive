---
title: "smbclient fault with Kerberos"
date: 2015-11-06
forum: Networking &amp; Wireless
---

### Post by marcio9 on 2015-11-06
Hello guys.
I have a problem with Ubuntu 14.04 (other machine with Fedora 22 is okay).
I'm trying connect to my free-IPA. When I execute "#smbclient -k //server/share_name" I have this error:

Doing kerberos session setup
krb5_init_context failed (invalid argument)
cli_session_setup_kerberos: spnego_gen_krb5_negTokenInit failed: invalid argument
SPNEGO login failed: Undetermined error
session setup failed: NT_STATUS_UNSUCCESSFUL

-The machine have Kerberos 5 1.12.
-klist and kinit works okay.

Here my krb5.conf:
#File modified by ipa-client-install

includedir /var/lib/sss/pubconf/krb5.include.d/

[libdefaults]
  default_realm = OTHERNAME
  dns_lookup_realm = true
  dns_lookup_kdc = true
  rdns = false
  ticket_lifetime = 24h
  forwardable = yes

[realms]
  OTHERNAME = {
    pkinit_anchors = FILE:/etc/ipa/ca.crt
  }

[domain_realm]
  .othername = OTHERNAME
  othername = OTHERNAME

[logging]
 default = FILE:/var/log/krb5libs.log
 kdc = FILE:/var/log/krb5kdc.log
 admin_server = FILE:/var/log/kadmind.log

I apreciate any help, thank you in advance.

---

### Post by roodjuriy on 2016-03-09
I have the same problem. Did you solve it?

---

