---
title: "configuring thunderbird for workstations on a samba pdc"
date: 2013-09-26
forum: Networking &amp; Wireless
---

### Post by tadewosa on 2013-09-26
I want to use samba3 pdc on ubuntu 12.04 server. I have set 10 workstations. Users change from workstation to workstation daily, and need access to email via thunderbird.
I am wondering whether it is possible to configure thunderbird that users access their mails using e-mail client independet of the machine they are logon.
Thanks

---

### Post by SeijiSensei on 2013-09-27
You didn't tell us what operating system is running on the client workstations.  That makes a big difference.

If they are running Ubuntu or some other *nix flavor, you should probably avoid Samba and use a more traditional Unix networking approach with NFS to export shares and NIS or LDAP to manage authentication. Users would be able to log in anywhere and have their home directories mounted over NFS.  Since all the Thunderbird configurations reside in $HOME/.thunderbird, the users would have the same view of their mail regardless of the machine they use.

If the machines are running Windows, then I have no idea how to do this.  I know there are things like "roving profiles" and other methods to mount the home directories, usually as drive H.  Beyond that, you should probably talk to someone who knows about Windows networking.

---

### Post by tadewosa on 2013-09-29
thank you. the question refers to windows 8.

---

