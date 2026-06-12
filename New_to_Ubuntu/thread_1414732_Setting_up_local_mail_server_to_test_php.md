---
title: "Setting up local mail server to test php"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by iammatic on 2010-02-23
I am using my local machine ip address to test my php code. I was learning how to send an email from a form. I have all the code correct on the php side. When I did some research I found out I needed to install a mail server so I installed postfix and dovecot. I am still not receiving the email. Is there something I need to specifically do since I am using my local machine to test the code? Is it even possible to send an email from a form when you are testing php from your local ip address? Any help would be appreciated.

iammatic

---

### Post by byStanderone on 2010-02-24
...well, id guess that would defend on what kind of internet service you have, whether it is static or dynamic, and whether your service provider allows the needed port to be opened.

---

### Post by mvalviar on 2010-02-24
If you're just testing to see if your php code works just send the mail to your local mail it's yourusername@localhost. To check your mail you can set up evolution to check it. Fire up evolution and set up a new account your email address is yourusername@localhost. For server type select 'Local delivery'. The path of your mailbox is /var/mail/yourusername.

I find it difficult to set up and out going mail server. For one the port might be blocked by your ISP etc, etc.

If you really want your mail to go out in the wilderness of the web you can use gmail's smtp server. You may send out 500 mails a day using it. Search google for 'smtp.gmail.com php fsocketopen' to learn more.

Cheers

---

### Post by iammatic on 2010-02-24
Okay so I tried to send the email to my username@localhost. This did not work either. When I was setting up my localhost email address in evolution I did not have my username to pick from for the path of my mailbox. I went to var/mail and there was only a file named www-data. I selected this file as path to my mailbox and as I suspected this did not work. Any ideas? Thanks

---

