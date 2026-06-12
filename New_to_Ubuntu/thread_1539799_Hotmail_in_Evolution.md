---
title: "Hotmail in Evolution?"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-07-27
What are the configurations to set it up?  I usually use thunderbird, but I like the huge integration with Evolution so I thought I'd give it a try.

---

### Post by Blackbird_13 on 2010-07-27
This works for me:

Receiving
pop3.live.com
[EMAIL="name@hotmail.com"]name@hotmail.com[/EMAIL]
SSL encryption
password: check for supported types

Sending
smtp.live.com:587
tick server requires authentication
TSL encryption
Authentication: plain, check for supported types

Best of luck

---

### Post by gandaran on 2010-07-27
> **TriBlox6432 said:**
> What are the configurations to set it up?  I usually use thunderbird, but I like the huge integration with Evolution so I thought I'd give it a try.
very easy, start the new account wizard, type in your hotmail email, select pop server, evolution will automatically fill in the pop and smtp details for hotmail, all you have to do is enable SSL encryption and in the username field type the full hotmail email, it wont work with just the username, thats all.

---

### Post by VH-BIL on 2010-07-27
You should be able to set up IMAP in hotmail as well.

---

### Post by TriBlox6432 on 2010-07-27
Thanks!! I got it all setup.

---

