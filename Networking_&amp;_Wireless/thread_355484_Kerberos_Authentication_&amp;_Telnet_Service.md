---
title: "Kerberos Authentication &amp; Telnet Service"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by lukesky on 2007-02-07
Hi, I'm working with Kerberos on my Ubuntu 6.10.

I have installed the krb5 packages and configurated the kdc.conf and krb5.conf files. The files are configurate to test the authentication on my local machine.

Now I am trying to active some kerberized service like telnet but I have some problem.

So I've exec thi steps:

1) Configure the /etc/hosts file:
127.0.1.1 laptop
192.168.182.254 kdc.epiluke.it admin.epiluke.it lukesky.epiluke.it
127.0.0.1 localhost localhost.localdomain

and I have configured the /etc/hostname file with this name "lukesky.epiluke.it"

2) Configure krb5.conf file:

[libdefaults]
	default_realm = EPILUKE.IT
.
.
[realms]
	EPILUKE.IT = {
		kdc = kdc.epiluke.it:88
		admin_server = admin.epiluke.it:749
	}
.
.
[domain_realm]
	.epiluke.it = EPILUKE.IT
	epiluke.it = EPILUKE.IT
.
.

3) Configure kdc.conf file:

[kdcdefaults]
    kdc_ports = 750,88

[realms]
    EPILUKE.IT = {
        database_name = /var/lib/krb5kdc/principal
        admin_keytab = FILE:/etc/krb5kdc/kadm5.keytab
        acl_file = /etc/krb5kdc/kadm5.acl
        key_stash_file = /etc/krb5kdc/stash
	
	kadmin_port = 749

        max_life = 10h 0m 0s
        max_renewable_life = 7d 0h 0m 0s
        master_key_type = des3-hmac-sha1
        supported_enctypes = des3-hmac-sha1:normal des-cbc-crc:normal des:normal des:v4 des:norealm des:onlyrealm des:afs3
        default_principal_flags = +preauth
    }

4) Then I have created a db:
$/usr/sbin/kdb5_util create -r EPILUKE.IT -s

5) I have created on /etc/krb5kdc directory a new ACL file (kadm5.acl) with this rules:

*/admin@EPILUKE.IT	*
*/*@EPILUKE.IT		i

6) I have execute kadmin.local:
>addpol -maxlife "180 days" -minlength 8 -minclasses 3 -history 3 user
>addpol -maxlife "90 days" -minlength 10 -minclasses 3 -history 6 admin
>addprinc -policy admin +requires_preauth krbadm/admin
>addprinc -policy user pippo
>ktadd -k /etc/krb5kdc/kadm5.keytab kadmin/admin kadmin/changepw

7) I have started the server

$/etc/init.d/krb5-kdc restart
$/etc/init.d/krb5-admin-server restart

8) I have tested the servers:

$kadmin -p krbadm/admin -> OK
$kinit pippo -> OK

Now I would configure kerberized telnet service but it doesn't work; there is something wrong.

9) From kadmin I have defined:

>addprinc host/lukesky.epiluke.it@EPILUKE.iT
>ktadd -k /etc/krb5.keytab host/lukesky.epiluke.it@EPILUKE.IT (??? I'm not sure that it's correct)

10) I create a new file in /etc/xinet.d/ directory named telnet:

service telnet
{
	socket_type	= stream
	wait		= no
	nice		= 10
	user		= root
	server		= /usr/sbin/telnetd
	server_args	= -h
}

11) I have restarted services

$ /etc/init.d/xinetd restart

Well, at this point I have exec by shell this command:

$telnet -l pippo lukesky.epiluke.it

but the results are:
Trying 192.168.182.254...
Connected to admin.epiluke.it (192.168.182.254).
Escape character is '^]'.
Password for pippo: 
Login incorrect

if I insert the password the system don't identify the credentials (that instead work on kinit command) and I can't entry on telnet service. 

Why? 

What can I do?

Can you help me? I'm crazying!

Thanks.

---

