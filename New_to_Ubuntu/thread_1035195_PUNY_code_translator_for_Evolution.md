---
title: "PUNY code translator for Evolution"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by suomalainen on 2009-01-09
Ubunteros,

I have an email address that contains a special character, i.e. "ä".

However, when I send test emails to myself using this special character they all get bounced back.

My ISP says that my email client, which in this specific case is Evolution, doesn't have a PUNY code converter that will translate this special character into the correct format required by the mail server.

Does anyone know what I need to install to get this working?

Thanks!!!!

---

### Post by Dark Aspect on 2009-01-09
> **suomalainen said:**
> Ubunteros,

I have an email address that contains a special character, i.e. "ä".

However, when I send test emails to myself using this special character they all get bounced back.

My ISP says that my email client, which in this specific case is Evolution, doesn't have a PUNY code converter that will translate this special character into the correct format required by the mail server.

Does anyone know what I need to install to get this working?

Thanks!!!!

I am not sure and it might not work but you could try

```
sudo apt-get install libidna-punycode-perl
```

---

### Post by Dedoimedo on 2009-01-09
Hi there,

Maybe you can try using UTF-8 encoding when sending your mails. Or write text in a text editor and then convert?

In general, I always use plain ascii when writing mails. It helps with whatever incompatibility there may be on the yonder side.

P.S. Don't listen to your ISP too much. In your place, I'd demand that they fix their poorly compliant mail servers and filters.

Dedoimedo

---

### Post by Hospadar on 2009-01-09
you might also try using thunderbird, if you install thunderbird, thunderbird-gnome-support, and lightning-extension (I might be wrong on the name of the last one, it's the calendar addon for thunderbird) you can get basically the exact same functionality as evolution.  I don't *know* that thunderbird will be any better about handing the strange characters, but it's always worth a try if you can't get it happening in evolution.

---

