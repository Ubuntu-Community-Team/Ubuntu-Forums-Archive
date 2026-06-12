---
title: "Kerberos logging"
date: 2018-10-11
forum: Networking &amp; Wireless
---

### Post by Hans_van_Leeuwen on 2018-10-11
We use Samba on Ubuntu 16.
Samba is configured with a realm and a domain on a Windows DC as workgroup (workgroup = <domain name>
Therefore also Kerberos is used.
According to the URL  [https://web.mit.edu/kerberos/krb5-1.4/krb5-1.4.1/doc/krb5-admin/logging.html#logging](https://web.mit.edu/kerberos/krb5-1.4/krb5-1.4.1/doc/krb5-admin/logging.html#logging)
the file /etc/krb5.conf contains the lines:
[logging]
            default = FILE:/var/log/krb5libs.log
            kdc = FILE:/var/log/krb5kdc.log
            admin_server = FILE:/var/log/kadmind.log

Kerberos is initialised with "sudo kinit administrator" and joined to the domain with "sudo net ads join -U administrator".
"klist" give correct result and Samba works fine. A Windows system can map a network drive from the Samba server.
But the files /var/log/krb5libs.log and /var/log/kadmind.log are not created, also when I use a wrong password.
Why is nothing logged for Kerberos?

---

