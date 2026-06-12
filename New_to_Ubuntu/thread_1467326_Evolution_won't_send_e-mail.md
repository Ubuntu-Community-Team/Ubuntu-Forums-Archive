---
title: "Evolution won't send e-mail"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by tonsil on 2010-04-30
I have a gmail account and evolution retrieves e-mails nicely, but whenever I try to send e-mails it fails. This is the error message:

Error while Sending message.

MAIL FROM command failed: Authentication Required. Learn more at                              
[http://mail.google.com/support/bin/answer.py?answer=14257](http://mail.google.com/support/bin/answer.py?answer=14257) 14sm1509354ewy.14

I've clicked the above link, unfortunately the page is not available.
Any help is most appreciated. Thank you!

---

### Post by howefield on 2010-04-30
Have a look at Edit > Preferences > Mail Accounts > Receiving Email tab, is Security set to SSL encryption ?

---

### Post by spiky001 on 2010-04-30
have a look at this

[http://ubuntuforums.org/showthread.php?t=1305906](http://ubuntuforums.org/showthread.php?t=1305906)

---

### Post by tonsil on 2010-04-30
I did. But with all respect I found it quite a bit off-topic. I couldn't find anything related to evolution??

---

### Post by tonsil on 2010-04-30
Success! I had a problem with sending e-mail so I went to Edit->Preferences->Sending email. Checked Server requires authentication -> use secure connection = TLS encryption. And now it works!

---

### Post by spiky001 on 2010-04-30
is you r evolution set up the same as in thread 7 ?

---

### Post by Monkey Horde on 2011-09-16
> **tonsil said:**
> Success! I had a problem with sending e-mail so I went to Edit->Preferences->Sending email. Checked Server requires authentication -> use secure connection = TLS encryption. And now it works!

Thanks a lot!

---

