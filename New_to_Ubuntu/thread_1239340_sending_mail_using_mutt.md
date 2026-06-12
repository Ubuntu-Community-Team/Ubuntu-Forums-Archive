---
title: "sending mail using mutt"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by bhargava470 on 2009-08-13
Hi all,

I am using mutt to send mail .... everything was fine till yesterday ... 
now this is showing this error 
          "errormsg='TLS certificate verification failed: the certificate hasn?t got a known issuer' exitcode=EX_UNAVAILABLE"

(i think this is happening after a fetchmail update yesterday...!!!!!!!!! )  

Here is the complete message in the .msmtp.log 
Aug 13 08:08:49 host=smtp.gmail.com tls=on auth=on user=****** from=****** recipients=******* errormsg='TLS certificate verification failed: the certificate hasn?t got a known issuer' exitcode=EX_UNAVAILABLE 

what is the problem .... any ideas are appreciated.

Thanks.

---

### Post by afroman10496 on 2009-08-13
Sorry, i dont know what mutt is:( is it an app or a mail service?

---

### Post by Hospadar on 2009-08-13
> **Afroman10496 said:**
> Sorry, i dont know what mutt is:( is it an app or a mail service?
Arr, it be a terminal mail client for l33t h4x0rz

Um, in all seriosness.
I'm not sure about the mutt issue, but have you tried pine, or another client to make sure it's a mutt problem and not the server?
Also if you know where mutt keeps it's tls keys, maybe you can try clearing out the cache?  Perhaps there is an old key that does not play nice with the new one.

---

### Post by bacardiandwatermelon on 2009-08-13
> **Hospadar said:**
> Arr, it be a terminal mail client for l33t h4x0rz

Is that a pirate impression?

---

### Post by afroman10496 on 2009-08-13
> **bacardiandwatermelon said:**
> Is that a pirate impression?
No, because he forgot the "gh" at the end of "arr". :P

---

### Post by andrew.46 on 2009-08-13
Hi bhargava,

> **bhargava470 said:**
> 
```

Aug 13 08:08:49 host=smtp.gmail.com tls=on 
auth=on user=****** from=****** recipients=******* 
errormsg='TLS certificate verification failed: the certificate hasn?t got a known issuer' 
exitcode=EX_UNAVAILABLE 
```


Looks like gmail have a bit more turbulence with their certificates and this time it looks like the smtp no longer accepts the Thawte certificate and now will only work with the Equifax certificate. An easy way under Ubuntu is simple to reference your .msmtprc file to the *ca-certificates *which are available from the repository. Your .msmtprc file would then contain:

```

tls on                       
tls_starttls on              
tls_trust_file /etc/ssl/certs/ca-certificates.crt

```

and this should ensure that even if the certs change yet again you should be right. Hope this helps?

Andrew

---

### Post by bhargava470 on 2009-08-13
Thanks andrew , It worked.

---

### Post by andrew.46 on 2009-08-13
Hi bhargava,

> **bhargava470 said:**
> Thanks andrew , It worked.

Great news :-). Google had a similar problem last year when some luckless employer forgot to renew the certificate, it will be interesting to see if there has been a similar problem now.

All the best,

Andrew

---

