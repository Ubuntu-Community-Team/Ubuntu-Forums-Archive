---
title: "Problem sending emails with mutt and sendmail"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by Maclor on 2010-11-11
I can send emails as root and when I go into mutt as root it connects to  gmail's smtp servers but if I am a normal user (in this case Nagios) it  does not connect to gmail's smtp server and will try to send it as  [email]nagios@sendemail@gmail.com[/email] instead of the [email]sendmail@gmail.com[/email] account I  have set up. Any help is greatly appreciated.

---

### Post by Maclor on 2010-11-11
Tried using sudo hoping it would be a little work around but then it just does [email]root@sendingemail@gmail.com[/email]. Really have no idea why it puts the user in front of the email but if anyone knows it should fix it I hope. It only does this for normal users and not root.

---

### Post by toekneewood on 2010-11-11
I think you need to make sure that you have a ".muttrc" file inside your own profile.  so if you login as yourself and copy the contents or root's ".muttrc" to your own.
```

touch ~/.muttrc ; sudo cat /root/.muttrc > ~/.muttrc

```

the .muttrc should look something like this
```

set imap_user = "yourname@gmail.com"
set imap_pass = "YOUR-PASSWORD"
 
set smtp_url = "smtp://yourname@smtp.gmail.com:587/"
set smtp_pass = "YOUR-PASSWORD"
set from = "yourname@gmail.com"
set realname = "Your Name"
 
set folder = "imaps://imap.gmail.com:993"
set spoolfile = "+INBOX"
set postponed="+[Gmail]/Drafts"

```

---

### Post by toekneewood on 2010-11-11
to send a test email.  And "email-address@hotmail.com" needs to be a real email address
```

echo "Test" | mutt -s Hello email-address@hotmail.com

```

---

### Post by Maclor on 2010-11-11
> **toekneewood said:**
> I think you need to make sure that you have a ".muttrc" file inside your own profile.  so if you login as yourself and copy the contents or root's ".muttrc" to your own.
```

touch ~/.muttrc ; sudo cat /root/.muttrc > ~/.muttrc

```the .muttrc should look something like this
```

set imap_user = "yourname@gmail.com"
set imap_pass = "YOUR-PASSWORD"
 
set smtp_url = "smtp://yourname@smtp.gmail.com:587/"
set smtp_pass = "YOUR-PASSWORD"
set from = "yourname@gmail.com"
set realname = "Your Name"
 
set folder = "imaps://imap.gmail.com:993"
set spoolfile = "+INBOX"
set postponed="+[Gmail]/Drafts"

```

Thanks. That got me being able to send the email as my user. Now I just have to get it working with nagios sending the notification which shouldn't be too difficult. Famous last words.

---

