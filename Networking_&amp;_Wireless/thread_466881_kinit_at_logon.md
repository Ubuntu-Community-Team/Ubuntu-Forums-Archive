---
title: "kinit at logon"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by corbouk on 2007-06-07
Hi,

I currently have ubuntu 7 authenticating against an AD server at logon.  I cannot however browse the shared folders on the server until I have either re-entered my password when prompted, or used kinit and my password to get a kerberos ticket.

Is it possible to get kinit to run at logon using the same credentials already entered, to avoid this extra password prompt?

Kind regards
Corbo!

---

### Post by Doc_symbiosis on 2007-07-12
I'm not sure about Winbind, but just brought Kerberos to run. I've added
```

auth sufficient pam_krb5.so forwardable
auth required pam_unix.so nullok_secure

```
to the /etc/pam.d/common-auth

```

password sufficient pam_krb5.so use_authtok
password sufficient pam_unix.so ...

```
to the /etc/pam.d/common-password.

So, in your case, I think, you've got to add the same, but replace the pam_krb5.so with pam_winbind.so.

Like I said, I'm not sure about this, but it's worth a try.

---

