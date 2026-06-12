---
title: "Posting Emails"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by Dai Bando on 2010-06-04
I have just this past week installed Lucid Lynx 10.04 but every time I try to send an email in Thunder bird SMTP times out and the only way I can send is via Google. Any ideas chaps?:(

---

### Post by howefield on 2010-06-04
Are you setting it to TLS/SSL ?

Can't remember exactly which you need.

---

### Post by Dai Bando on 2010-06-04
> **howefield said:**
> Are you setting it to TLS/SSL ?

Can't remember exactly which you need.
It is set as it always has been to my knowledge.

---

### Post by wojox on 2010-06-04
Is it set to port **995**

---

### Post by Dai Bando on 2010-06-04
> **wojox said:**
> Is it set to port **995**
It is set to port 587!

---

### Post by LowSky on 2010-06-04
Dont worry it is supposed to be at 587
[http://mail.google.com/support/bin/answer.py?hl=en&answer=77662](http://mail.google.com/support/bin/answer.py?hl=en&answer=77662)


Did you enable IMAP in Gmail?
[http://mail.google.com/support/bin/answer.py?answer=77695](http://mail.google.com/support/bin/answer.py?answer=77695)

---

### Post by howefield on 2010-06-04
> **LowSky said:**
> Dont worry it is supposed to be at 587

That's interesting.

Just installed Thunderbird to take a look, the account wizard asked for name, email address, and password then auto configured everything else including port 465 for smtp.

All works fine.

---

### Post by Dai Bando on 2010-06-04
> **LowSky said:**
> Dont worry it is supposed to be at 587
[http://mail.google.com/support/bin/answer.py?hl=en&answer=77662](http://mail.google.com/support/bin/answer.py?hl=en&answer=77662)


Did you enable IMAP in Gmail?
[http://mail.google.com/support/bin/answer.py?answer=77695](http://mail.google.com/support/bin/answer.py?answer=77695)
I have changed the port to 25 and everything is now OK. Thank you very much.

---

