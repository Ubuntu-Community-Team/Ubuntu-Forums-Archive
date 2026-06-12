---
title: "public key problem with R"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by myotis on 2010-04-03
I am trying to install the public key for R but get the following error.

graham@eeepc-linux ~ $ gpg --keyserver subkeys.pgp.net --recv-key E2A11821
gpg: requesting key E2A11821 from hkp server subkeys.pgp.net
gpg: can't open `/home/graham/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0

I wondered if it just needed sudo but this gives me

graham@eeepc-linux ~ $ sudo gpg --keyserver subkeys.pgp.net --recv-key E2A11821
[sudo] password for graham:
gpg: WARNING: unsafe ownership on configuration file `/home/graham/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error


This is actually on Linux Mint 8 (and I have also asked on the Mint forums) but I assume it will be the same as Ubuntu 9.10.  It did however, work fine on Ubuntu 9.10 on my Thinkpad, but not here with Mint on an Asus eeepc 901

Thanks,

Graham

---

### Post by Bachstelze on 2010-04-03
```
gpg: can't open `/home/graham/.gnupg/pubring.gpg'
```

Probably wrong permissions. Paste the output of

```
ls -l /home/graham/.gnupg/pubring.gpg
```

---

### Post by myotis on 2010-04-03
Thanks,

Printout below

graham@eeepc-linux ~ $ ls -l /home/graham/.gnupg/pubring.gpg
-rw------- 1 root root 0 2009-07-11 10:00 /home/graham/.gnupg/pubring.gpg


Graham

---

### Post by myotis on 2010-04-03
This has now been sorted by manually downloading the key file and installing locally, but I would still be interested in any light on why it didn't work as it has worked many times before.

Graham

---

### Post by Bachstelze on 2010-04-03
It didn't work because the file was owned by root and not readable or writable by anyone else. This is why gpg couldn't access it while running as a normal user.

---

### Post by myotis on 2010-04-03
I thought that running the command with sudo over came this, or I misunderstanding what running as root means?

Graham

---

### Post by Bachstelze on 2010-04-03
Bottom-line is: you should not have any file owned by root in your home directory. If you do, you will have a lot of problems like that.

---

### Post by myotis on 2010-04-03
Is that a mix up with permissions then, as I have done this at least a dozen times in the past with fresh installs when I add the R repository to Synaptic and this is the first time it hasn't just worked.

I have always just followed the instructions as I did this time, but this time I got the errors I posted. So can I assume that in the past the file hasn't been owned by root and somehow it now is?

Should I change the permissions?

Graham

---

### Post by Bachstelze on 2010-04-03
> **myotis said:**
> 
Should I change the permissions?

Yes, or rather change the owner:

```
sudo chown graham:graham /home/graham/.gnupg/*
```

---

### Post by myotis on 2010-04-03
Thanks, I will do that. I see that the files on my Thinkpad (with Ubuntu 9.10) have the files owned by the User, so I will do as you say.

Graham

---

