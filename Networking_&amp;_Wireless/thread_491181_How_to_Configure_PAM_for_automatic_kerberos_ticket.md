---
title: "How to Configure PAM for automatic kerberos ticket (kinit)?"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by evilkernel on 2007-07-03
Hi -

I used the tutorial found here [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto ]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto") to succesfully configure SAMBA, Winbind and PAM on 7.04 desktop.  The machine joined my W2K3 domain and authenticates properly, however, I would like for it to obtain kerberos tickets automatically and the PAM tutorial above is not set for that.  

So, as a result,  I am having to do a kinit manually upon loggin in and then a kdestroy upon loggin out.  While I realize I could setup a login/logoff script to accomplish this, I know there is a way to configure PAM to use kerberos for obtaining tickets automatically.

Can anyone she some light on this?

Many thanks in advance!

---

### Post by Doc_symbiosis on 2007-07-12
I'm not sure about Winbind, but just brought Kerberos to run. I've added
```

password sufficient pam_krb5.so use_authtok
password sufficient pam_unix.so ...

```
to the /etc/pam.d/common-password.

So, in your case, I think, you've got to add the same, but replace the pam_krb5.so with pam_winbind.so.

Like I said, I'm not sure about this, but it's worth a try.

---

