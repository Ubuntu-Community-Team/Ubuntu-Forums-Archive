---
title: "GPG Errors :: Cannot update installation"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by DaveGiant on 2009-10-24
When I check for updates I get the following errors.

```
W: GPG error: http://deb.opera.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061
W: GPG error: http://ftp.debian.org etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B
```

How do I resolve these errors so I can get updates again?

---

### Post by SkyNet2029 on 2009-10-24
For the Debian key issue this command:
 
```
$**gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 9AA38DCD55BE302B**

```
then
```
$**apt-key add .gnupg/pubring.gpg**

```
 
For the Opera key issue this command:
 
```
$ gpg --recv-keys F9A2F76A9D1A0061
```
then
```
$ gpg --export -a 9D1A0061|apt-key add -
```
then 
```
$apt-get update
```

---

### Post by DaveGiant on 2009-10-24
Thanks for the speedy reply.

Unfortunately neither the 2nd nor 4th command worked. Here is my log from running the commands.

```
jason@ubuntu:~$ $gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 9AA38DCD55BE302Bbash: --keyserver: command not found
jason@ubuntu:~$ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 9AA38DCD55BE302Bgpg: keyring `/home/jason/.gnupg/secring.gpg' created
gpg: keyring `/home/jason/.gnupg/pubring.gpg' created
gpg: requesting key 55BE302B from hkp server wwwkeys.eu.pgp.net
gpg: /home/jason/.gnupg/trustdb.gpg: trustdb created
gpg: key 55BE302B: public key "Debian Archive Automatic Signing Key (5.0/lenny) <ftpmaster@debian.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
jason@ubuntu:~$ apt-key add .gnupg/pubring.gpg
gpg: no writable keyring found: eof
gpg: error reading `.gnupg/pubring.gpg': general error
gpg: import from `.gnupg/pubring.gpg' failed: general error
jason@ubuntu:~$ gpg --recv-keys F9A2F76A9D1A0061
gpg: requesting key 9D1A0061 from hkp server keys.gnupg.net
gpg: key 9D1A0061: public key "Opera Software Archive Automatic Signing Key 2010 <packager@opera.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
jason@ubuntu:~$ gpg --export -a 9D1A0061|apt-key add -
gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error
jason@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
jason@ubuntu:~$ 
```

Updates still fail.

Help, as ever, is much appreciated.

---

### Post by oldos2er on 2009-10-24
```
sudo apt-get update
```

---

