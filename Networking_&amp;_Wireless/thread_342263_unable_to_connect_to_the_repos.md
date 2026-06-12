---
title: "unable to connect to the repos"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by bender5788 on 2007-01-19
Ok ive got something strange going one here as of two days ago the repos have started refusing my connections or at least that is what the error messages are reporting. The strange part is that i can ping them, i can connect to them via the browser in this case firefox 1.5 but i can not reach it via apt-get , synaptic (a given considering its just an apt-get gui) and aptitude. The error message is as follows for each of the following programs.
**Synaptic:*** Connect (111 Connection refused)*

**apt-get:**
[I]Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main samba 3.0.22-1ubuntu3.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.22-1ubuntu3.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.22-1ubuntu3.1_amd64.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

[/I][B]aptitude:
[/B][I]Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main libconvert-asn1-perl 0.19-1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe libdigest-md4-perl 1.5-1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main libdigest-sha1-perl 2.10-1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main samba 3.0.22-1ubuntu3.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main libnet-ssleay-perl 1.25-2build1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main libio-socket-ssl-perl 0.97-2build1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe libjcode-pm-perl 2.03-1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main libnet-ldap-perl 1:0.33-2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe libunicode-map-perl 0.112-9
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe libunicode-map8-perl 0.12-2
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe libunicode-maputf8-perl 1.09-6
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe libcrypt-smbhash-perl 0.12-1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe smbldap-tools 0.9.2-3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main samba-doc 3.0.22-1ubuntu3.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main swat 3.0.22-1ubuntu3.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)



Ok the problem was stemming from a corrupt sources file combined with a router error  as for how i fixed it... Replaced the sources file then did an update using the update manager (would connect despite being apt based) followed by a reset on the router.[/I]

---

