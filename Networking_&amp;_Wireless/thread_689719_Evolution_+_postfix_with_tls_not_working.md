---
title: "Evolution + postfix with tls not working"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by Nicklas Overgaard on 2008-02-06
Hello everyone,

I just followed [this]("https://help.ubuntu.com/community/Postfix") guide which helped me installing postfix on my ubuntu 7.10 server.

When i try to login using evolution, i get the following error:

"Error while performing operation. 
STARTTTLS command failed: TLS not available due to local problem"

What does that mean? Is it a problem on my client machine with evolution, or something i got wrong when setting up my server?

I followed the guide step-by-step, copy pasting everyting. The only change i have made, is using shadow instead of pam as the authentication store.

btw. im using evolution 2.12.1 and postfix 2.4.5-3ubuntu

Thanks in advance,

Nicklas.

---

### Post by Nicklas Overgaard on 2008-02-16
I managed to fix this.

I had to add the following to my master.cf file:

```
smtps    inet  n  -  n  -  -  smtpd -o smtpd_tls_wrappermode=yes -o smtpd_sasl_auth_enable=yes
587  inet  n  -  -  -  -  smtpd -o smtpd_enforce_tls=yes -o smtpd_sasl_auth_enable=yes
```

---

