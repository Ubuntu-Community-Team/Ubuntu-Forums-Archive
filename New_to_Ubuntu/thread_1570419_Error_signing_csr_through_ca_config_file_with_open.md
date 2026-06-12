---
title: "Error signing csr through ca config file with openssl under 10.04.1 svr"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by mchonig on 2010-09-08
Hi gents, a question: I want to configure apache to accept self-signed client certificates as a means of authentication to access a website. I've got an openssl config file which I'm using in a test setup with an openssl CA. I've created the keypair for the CA, created a keypair for the webserver, signed the webserver csr and have generated a keypair for the client that needs to access the webserver with a client certificate. Now I'm trying to sign the client certificate with the CA certificate with the following command:

root@server$ openssl ca -config ~/ca/openssl.cnf -policy policy_anything -extensions ssl_client -out ~/ca/newcerts/user.clientcert.signed.pem -infiles ~/ca/requests/user.clientcert.csr.pem

I keep getting the following error:

Using configuration from ~/ca/openssl.cnf
error on line 9 of config file '~/ca/openssl.cnf'
1029:error:0E065068:configuration file routines:STR_COPY:variable has no value:conf_def.c:629:line 9

Looking up line 9 of openssl.cnf, it states:
RANDFILE = $ENV::SSLDIR/.rnd

Doing a little Googling I discovered these two posts that would seem to be related:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=465279](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=465279)
[http://us.generation-nt.com/answer/bug-584911-bind9-hard-coded-dependency-usr-lib-ssl-openssl-cnf-might-cause-trouble-help-198805381.html](http://us.generation-nt.com/answer/bug-584911-bind9-hard-coded-dependency-usr-lib-ssl-openssl-cnf-might-cause-trouble-help-198805381.html)

Thinking it might be some kind of path issue, I tried changing this to the absolute path (RANDFILE = $ENV::/home/user/ca/.rnd) but to no avail. Does anyone have an idea what I'm doing wrong? PS I know linux basics but that's about it, so please be gentle ;)  I have the latest version of ssl-cert installed.

---

### Post by mchonig on 2010-09-08
Fixed. I added the lines 

SSLDIR = /home/username/ca
HOME = .

to the top of openssl.cnf; I changed the RANDFILE line to

RANDFILE = $ENV::HOME/.rnd

and had to adjust the dir setting as well:

dir = $ENV::SSLDIR

After that it worked like a charm =)

---

