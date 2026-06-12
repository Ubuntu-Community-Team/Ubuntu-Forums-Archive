---
title: "Guarddog not allowing incoming SSH"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by SadaraX on 2008-05-09
I am running Kubuntu Hardy 8.04 with Guarddog (version 2.6.0). I have been using Guarddog for years now and this is the first problem I have had like this.

After booting up, I cannot get Guarddog to allow incoming SSH connections until I restart the service, at which point it allows the connections.

I have tried everything, including remove ALL options except DNS and SSH for local and internet (with special ports defined for my SSH connection and in my /etc/ssh/sshd_config).

Like I said, if I restart the service using 'sudo invoke-rc.d guarddog restart' then I can connect. Help please.

---

### Post by Stebalien on 2008-05-28
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

Bump.
Same problem here.  As well as being unable to connect to my ssh server, I am unable to print.
sudo iptables -L reveals that my ssh port is open.
- --
Steven (Stebalien.com)
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.6 (GNU/Linux)

iD8DBQFIPgch2FSfVyUro4URAp98AKCTcgxIdrw77gjWzp7bqatKVNa2HACgtnSb
/LIMmwV69uoKHj9/eybYMBU=
=IZSt
-----END PGP SIGNATURE-----

Edit: I am using wicd as my network manager.

---

### Post by Stebalien on 2008-07-22
Bump.
Can anyone help?

---

### Post by f37u5g0d on 2008-07-22
Try putting that command in a start-up script.  I know it's only a workaround but it would make the problem seem to go away.

---

