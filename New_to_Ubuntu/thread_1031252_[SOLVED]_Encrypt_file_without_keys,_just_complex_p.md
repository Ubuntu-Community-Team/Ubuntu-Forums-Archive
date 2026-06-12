---
title: "[SOLVED] Encrypt file without keys, just complex password from cmd line"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by batfastad on 2009-01-05
Hi everyone

I've been learning Linux using Ubuntu Server for about 6 months now. Build a RAID NAS and configured Samba/Netatalk and have also moved our intranet Apache/PHP/MySQL services from Windows and onto Ubuntu Server. All going well.

Just wondering, what's the best way to encrypt a single file through the command line?

I'm writing a command line PHP script to backup our MySQL databases, compress them into 7z format, encrypt them then upload them to a private FTP server.
Ideally I want to be able to pass a complex password to the program from the command line.

I've been reading up on the gpg utility, but it seems to be quite email encryption focused. All I'm looking to do with gpg on this server is to encrypt/decrypt files with a complex password.

What's the purpose of the key?
Is to allow decryption by only certain computers?

I'd like to be able to decrypt the files by just supplying the password.

Is gpg what I want?
Or are there other utilities I should be looking at?

Cheers, B

---

### Post by batfastad on 2009-01-05
Ok solved!
gpg will do exactly what I need, with the --symmetric switch it will prompt for a passphrase.
Then to pass a passphrase using the command line I used the --passphrase option

Hope this helps someone out ;)

---

