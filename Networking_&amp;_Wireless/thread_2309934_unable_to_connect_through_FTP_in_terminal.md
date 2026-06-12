---
title: "unable to connect through FTP in terminal"
date: 2016-01-14
forum: Networking &amp; Wireless
---

### Post by Julio_Lyfeld on 2016-01-14
i'm trying to configure FTP Server but i got these error or message upon logging in from the terminal:

**Name (172.16.1.201:user): user**
**530 Non-anonymous sessions must use encryption.**
**Login failed.**
**421 Service not available, remote server has closed connection**




this is also the contents of my **/etc/vsftpd.conf**:


[B]# encrypted connections.
#rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_cert_file=/etc/ssl/private/vsftpd.pem
#rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
rsa_private_key_file=/etc/ssl/private/vsftpd.pem
#ssl_enable=NO
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO


require_ssl_reuse=NO
ssl_ciphers=HIGH


#seccomp_sandbox=NO[/B]



hoping for an assistance or a good help.


cheers! ;)

---

