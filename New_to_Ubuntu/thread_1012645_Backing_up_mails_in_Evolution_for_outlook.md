---
title: "Backing up mails in Evolution for outlook"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by pinchbear on 2008-12-16
Hi all,

I am new to ubuntu. I installed it as dual boot with windows XP just to check it out. Then I configured our office Exchange server to Evolution. But I missed the setting "Leave messages on server". Because of that, when I synchronise evolution with exchange, it cleared the messages in server. But I have them in evolution. 
So is there a way to send those mails back to the server? Or to back these mails in a  format readable by Outlook?
Pls help
:confused:
Thanks in advance guys..

---

### Post by uniqueumang on 2008-12-16
Ever thought of downloading and installing  thunderbird . You can download it using synaptic package manager , and u can install on windows too :)

---

### Post by pinchbear on 2008-12-16
Yup,
I did it. But after configuring evolution. Now the problem is I dont have any mail in the server. How to get them??
Thanks for the reply mate.

---

### Post by uniqueumang on 2008-12-16
This is troubleshooting from gmail for thunderbird . I hope it helps.

[http://mail.google.com/support/bin/answer.py?hl=en&answer=38343](http://mail.google.com/support/bin/answer.py?hl=en&answer=38343)

---

### Post by hyper_ch on 2008-12-16
don't you have IMAP on the server? IMAP normally leaves mails on the server while "POP3 leaving mail on server" is just a "hack" IMHO.

---

### Post by pinchbear on 2008-12-16
Thanks for the help mate. I want retrieve my mails back to the server buddy. Any help regarding that?
Thanks

---

### Post by hyper_ch on 2008-12-16
if the server supports IMAP then it's fairly simple.

---

### Post by pinchbear on 2008-12-16
Ya. Server supports IMAP. Can I use it to synchronise the mails I have in evolution to the server?
Thanks.

---

### Post by hyper_ch on 2008-12-16
well, I assume you currently have all the mails downloaded. So I'd:

(1) setup another email account in evolution using IMAP
(2) disable automatic POP3 checking of the current account
then
(3) just drag and drop the emails from the evolution pop3 account into the according evolution IMAP account

That way the mails will be transferred back onto the server and email date, sender, recipient etc. will stay the same.

---

