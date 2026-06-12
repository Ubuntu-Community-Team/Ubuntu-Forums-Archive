---
title: "Newbiie need some help"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by Vincnt on 2011-01-26
I just purchased a dedicated server with Ubuntu Server 10.10 installed with DirectAdmin. They gave me the installer login information and I was able to login and change the password but somehow now I can't login anymore...it keep saying Access denied. 

Lucky I had root enabled which I can login into root and command << sudo passwd username >> with new password but I still get the Access denied...I'm pretty sure the password is 100% correct. Any ideas?:confused: Please help....thanks!

---

### Post by HermanAB on 2011-01-26
Howdy,

How do you log in, ssh?

If so, try this:
$ ssh -vvv user@serveripaddress

and look at the error messages.

---

### Post by Vincnt on 2011-01-26
I login using PUTTY: I follow your instruction and I get this:

root@server:~# ssh -vvv user@serveripaddress
OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
ssh: Could not resolve hostname serveripaddress: Name or service not known

---

