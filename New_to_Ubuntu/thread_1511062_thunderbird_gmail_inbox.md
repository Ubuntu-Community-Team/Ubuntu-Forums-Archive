---
title: "thunderbird gmail inbox"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by DarinB on 2010-06-16
how do i get the gmail to put the new mail in the local folders inbox
i can't find the option.
thunderbird 3.0.4

---

### Post by AsusEEEPC on 2010-06-16
[http://mail.google.com/support/bin/answer.py?answer=77662](http://mail.google.com/support/bin/answer.py?answer=77662)

This is for Thunderbird 2.0, but it should be similar to 3.0.4

---

### Post by DarinB on 2010-06-16
thanks but it does not answer the question.
anybody know how to have the mail go to the local folders inbox instead of the separate Gmail inbox???
i was able to do it with 2.0.0.2.2 but i do not see the tab for that here.

---

### Post by DarinB on 2010-06-21
figured this out now all mail goes to one mailbox 

Standard instructions:

   1. Enable POP in Gmail. Don't forget to click Save Changes when you're done.
   2. Configure your client to match the settings below:
      Incoming Mail (POP3) Server - requires SSL: 	pop.gmail.com
      Use SSL: Yes
      Port: 995
      Outgoing Mail (SMTP) Server - requires TLS or SSL: 	smtp.gmail.com (use authentication)
      Use Authentication: Yes
      Port for TLS/STARTTLS: 587
      Port for SSL: 465
      Account Name: 	your full email address (including @gmail.com or @your_domain.com)
      Email Address: 	your email address (username@gmail.com or [email]username@your_domain.com[/email])
      Password: 	your Gmail password

      Unless you're using recent mode to download mail to multiple clients, make sure you've opted not to leave messages on the server. Your Gmail settings determine whether or not messages stay on the server, so this setting in your client won't affect how Gmail handles your mail.

      Please note that if your client does not support SMTP authentication, you won't be able to send mail through your client using your Gmail address.

      Also, if you're having trouble sending mail but you've confirmed that encryption is active for SMTP in your mail client, try to configure your SMTP server on a different port: 465 or 587.
   3. You're now ready to use POP with your Gmail address.

Change the Advanced settings.
[ATTACH]161080[/ATTACH]

---

