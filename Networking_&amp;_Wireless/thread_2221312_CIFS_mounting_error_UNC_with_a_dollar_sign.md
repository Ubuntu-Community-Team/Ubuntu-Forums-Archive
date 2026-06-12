---
title: "CIFS mounting error UNC with a dollar sign"
date: 2014-05-01
forum: Networking &amp; Wireless
---

### Post by Featalene on 2014-05-01
I have several CIFS mounts in my fstab only the UNC that ends with a dollar sign fails. I have tried using the dollar sign bare, escaped with a backslash, and using an octal code. None have worked.
Example:
//server1.example.com/QAVM                              /QAVM                        cifs credentials=/home/dbaker/.smbcredentials,iocharset=utf8,sec=ntlm 0 0
//server1.example.com/dfshares/Corporate            /dfshares                     cifs credentials=/home/dbaker/.smbcredentials,iocharset=utf8,sec=ntlm 0 0
//server2.example.com/darryl.baker\044               /private_share              cifs credentials=/home/dbaker/.smbcredentials,iocharset=utf8,sec=ntlm 0 0
//server2.example.com/Information\040Technology /information_technology cifs credentials=/home/dbaker/.smbcredentials,iocharset=utf8,sec=ntlm 0 0

---

