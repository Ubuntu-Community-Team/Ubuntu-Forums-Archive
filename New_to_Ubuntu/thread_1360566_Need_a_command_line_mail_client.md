---
title: "Need a command line mail client"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by mvalviar on 2009-12-21
I trying to make a script that sends report to [email]someone@gmail.com[/email]. I need to be able to send this report using [email]mymail@gmail.com[/email]. How do I go about doing that?

---

### Post by VCoolio on 2009-12-21
You could use mutt: sudo apt-get install openssl mutt
Create a file ~/.muttrc containing:
```
set imap_user = "you@gmail.com"
set imap_pass = "passwordhere"

set smtp_url = "smtp://you@smtp.gmail.com:587/"
set smtp_pass = "passwordhere"
set from = "you@gmail.com"
set realname = "M. Valviar"

set folder = "imaps://imap.gmail.com:993"
set spoolfile = "+INBOX"
set postponed="+[Gmail]/Drafts"

set header_cache=~/.mutt/cache/headers
set message_cachedir=~/.mutt/cache/bodies
set certificate_file=~/.mutt/certificates

set move = no
```

Use commands like these:
echo "message" | mutt -a /file/to/attach -s "subject" [email]recipient@address.com[/email]
cat /file/with/message | mutt -a /file/to/attach -s "subject" [email]recipient@address.com[/email]

---

### Post by KeLa on 2009-12-21
Have you tried this:
```
mail -s 'Hai' somewhere@domain.com < /tmp/message
```

---

### Post by mvalviar on 2009-12-21
Ok. I'll give those a try.

---

### Post by t0p on 2009-12-21
When I had need of a way to send email from a script through a gmail account, I had to follow the steps outlined [here]("http://wiki.debian.org/GmailAndExim4"). The guide is written for Debian, but as I remember it's fine for Ubuntu too.  One thing: you may need to install **exim4**, as I don't think it comes by default with Ubuntu.

The guide is written for use in the terminal, but don't let that put you off.  It's pretty easy to follow.

---

