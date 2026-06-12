---
title: "SSH Problems"
date: 2015-04-02
forum: Networking &amp; Wireless
---

### Post by michael260 on 2015-04-02
Hello All.
So, a couple of weeks ago I tried to set-up OpenSSH with RSA keys, however, it failed horribly and I reinstalled Ubuntu, when I was configuring it, I did ssh-copy-id to another devices, now, after this, I sshed into that device, and it added a RSA key to my known_hosts, I thought, well that device was already soft of messed up there, however, today I got a new device I could ssh into, and it added a RSA key to my known_hosts, even though there was no files on Ubuntu or that device prompting this.  Before setting up openSSH and the reinstall, there were no problems. Please if possible, tell me what the problem is, and how to fix it.

---

### Post by papibe on 2015-04-02
Hi michael260.

I don't understand what the problem is.

Keys are created in pairs. The private key should remain on the client (the side that wants to connect to). The public key should be transfer to the the server (the side is receiving the remote connection), and be added to the file ~/.ssh/authorized_keys. The command ssh-copy-id automates the latter for you.

When you say you reinstalled, you may have destroyed the private key if you formated your home partition. If not, the key may be still there.

In case the private key was destroyed, that does not stop connections being made, just default them to use passwords.

Does that help? If not, could you explain your situation a little bit more?
Regards.

---

### Post by michael260 on 2015-04-02
Hello Papibe,
so, when I reinstalled, the home directory was formatted, destroying the key, my problem is, is that each time I connect to another device, a RSA key appears in my known_hosts file, instead of an IP address. It's a problem for me, and I need it fixed. I hope that you could tell me why this is happening. Thank you.

---

### Post by SeijiSensei on 2015-04-03
The known_hosts file no longer includes IP addresses to improve security.  There may be a way to force the SSH client to use the old format for known_hosts, but I don't know how.  Maybe you can find one by browsing the options with "man ssh_config".

---

### Post by Lars Noodén on 2015-04-03
michael260, what you might be seeing in *known_hosts* in the first column is a hash of the host name or IP number.  The idea there is that if the *known_hosts* file is read by an attacker, it can't be used to find further targets.  This is not the default in vanilla SSH but is on Debian and its derivatives like Ubuntu.  

> **SeijiSensei said:**
> The known_hosts file no longer includes IP addresses to improve security.  There may be a way to force the SSH client to use the old format for known_hosts, but I don't know how.  Maybe you can find one by browsing the options with "man ssh_config".

The way to turn it off is to set 'HashKnownHosts' to 'no' in ~/.ssh/[config](http://manpages.ubuntu.com/manpages/trusty/en/man5/ssh_config.5.html).  However, hashed hosts will stay hashed so they will have to be removed from the file if you want the IP number or host name in clear text.  [ssh-keygen](http://manpages.ubuntu.com/manpages/trusty/en/man1/ssh-keygen.1.html) can do that.  Otherwise, you have to look at the keys themselves in the third column when doing it manually.

---

