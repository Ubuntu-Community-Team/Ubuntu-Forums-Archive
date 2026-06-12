---
title: "Cant' see Fedora 8 Samba Shares"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by Frankly3D on 2008-01-07
Followed this:
[http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs](http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs)
Have autofs installed.
/cifs folder is there, but 
ls -als /cifs/Frank-00/share00
ls: /cifs/xxxx/yyyyy: No such file or directory

smbclient  //xxxx/yyyy
password: userwhatever

Shows fine
Any ideas?

New to xubuntu 7.10

Frank

---

### Post by glennzo on 2008-01-07
Hi Frank. I don't follow. You can't see what from where?

---

### Post by njparton on 2008-01-07
I found autofs a nightmare - try adding some cifs share entries to fstab instead.

---

### Post by Frankly3D on 2008-01-07
> **glennzo said:**
> Hi Frank. I don't follow. You can't see what from where?

Fedora 8 Samba Server.

Xubuntu client cannot see the share using autofs. (preference)
But if I use smblient they are there.

It may be a password problem, as my Xubuntu Box login p\w works.
Bur if I do sudo on a terminal I get an error:

xxxxx@yyyy-02:~/Desktop$ sudo updatedb
[sudo] password for xxxx:
Sorry, try again.
[sudo] password for xxxxx

Frank

---

