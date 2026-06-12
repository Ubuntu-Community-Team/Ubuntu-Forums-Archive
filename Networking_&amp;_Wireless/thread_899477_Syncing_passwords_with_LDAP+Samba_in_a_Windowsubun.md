---
title: "Syncing passwords with LDAP+Samba in a Windows/ubuntu mixed network"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by Warhog on 2008-08-24
Hi,

i'm setting up a school-network with roundabout 30 computers using ubuntu hardy and ebox. Everything works fine, the Windows-Clients authenticate against Samba, the Ubuntu-Clients authenticate against LDAP. But if a user changes the password in Ubuntu it is not synced with the Windows password, but the other way around.

I suppose it's luck that the passwords are synced when changed in windows cause samba does the syncing. But the other way around I haven't got any plan what to do further.

Til now I configured PAM that it uses pam_smbpass optionally, than I changed the smb.conf so that it uses ldapsam as passdb-backend. Before i did this /var/log/auth.log said something like this:
> Aug 24 16:12:16 INFO-11 passwd[7417]: pam_smbpass(passwd:chauthtok): Failed to find entry for user ela.

Now it says:
> Aug 24 16:13:25 INFO-11 passwd[7426]: pam_smbpass(passwd:chauthtok): username [ela] obtained
than "passwd" hangs and after a certain timeout it aborts - now again "failed to find entry..." is in the logfile.

What am I doing wrong? Do I have to change something in Sambas PAM-Configuration at /etc/pamd. ? It took me the whole afternoon and I didn't get any further than this.

thanks in advance, if someone of you has got an idea^^

greetings, Warhog

---

### Post by Warhog on 2008-08-25
no idea?

---

