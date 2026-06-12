---
title: "mutt not sending mail"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by karthick87 on 2010-10-03
I have installed mutt and postfix,and i tested it by  sending mails from my command line but i din receive any mails in my inbox..?What may be the problem..?

---

### Post by jtarin on 2010-10-03
Huh! Nobody wrote you?:)

How have you configured Mutt? POP, IMAP?

---

### Post by jtarin on 2010-10-03
Upon first installation you are shown this screen (attached)which configuration did you select?

---

### Post by karthick87 on 2010-10-03
> **jtarin said:**
> Upon first installation you are shown this screen (attached)which configuration did you select?

It din show any screen while installing mutt.

---

### Post by Hippytaff on 2010-10-03
did you sudo apt-get install mutt?

---

### Post by jtarin on 2010-10-03
Here's a [link]("http://lifehacker.com/5574557/how-to-use-the-fast-and-powerful-mutt-email-client-with-gmail") to show how to do a fast-setup

---

### Post by karthick87 on 2010-10-03
> **Hippytaff said:**
> did you sudo apt-get install mutt?

Yes.

---

### Post by Hippytaff on 2010-10-03
strange how the configuration screen didn't appear...maybe remove it and try again!?

---

### Post by jtarin on 2010-10-03
Try using Synaptic to remove an reinstall....

---

### Post by karthick87 on 2010-10-03
> **jtarin said:**
> Here's a [link]("http://lifehacker.com/5574557/how-to-use-the-fast-and-powerful-mutt-email-client-with-gmail") to show how to do a fast-setup


The above link helped me to configure mutt for sending and receiving mails.Thanks a lot :)

---

### Post by karthick87 on 2010-10-03
> **jtarin said:**
> Here's a [link]("http://lifehacker.com/5574557/how-to-use-the-fast-and-powerful-mutt-email-client-with-gmail") to show how to do a fast-setup


The above link helped me to configure mutt for sending and receiving mails.Thanks a lot :)

---

### Post by jtarin on 2010-10-03
> **getyourkarthick said:**
> The above link helped me to configure mutt for sending and receiving mails.Thanks a lot :)
Excellent...glad you found it useful.

---

### Post by karthick87 on 2010-10-03
How to attach a file in mutt..?

---

### Post by jtarin on 2010-10-03
[Time for you to do some reading]("http://www.mutt.org/doc/manual/manual.html#toc4").

---

### Post by Hippytaff on 2010-10-03
there should be an a option once you've started a new mail. will ask for a path to the file you want to attach...if its home/user then you don't need to specify the path.

but that link is full of the stuff I need to read up on too...cheers for that :-)

---

### Post by karthick87 on 2010-10-04
I have added the following code in .muttrc

```
ignore date *
unignore from subject to cc
unignore organization organisation x-mailer: x-newsreader: x-mailing-list:
unignore posted-to:

```

But still date can be viewed in mail..Is the above code not working..?

---

### Post by karthick87 on 2010-10-05
Bump...!

---

### Post by Hippytaff on 2010-10-05
can you post the full .muttrc? (obviously excluding passwords etc :-)

---

### Post by karthick87 on 2010-10-05
```
# A basic .muttrc for use with Gmail

# Change the following six lines to match your Gmail account details
set imap_user = "username@gmail.com"
set imap_pass = ""
set smtp_url = "smtp://username@smtp.gmail.com:587/"
set smtp_pass = ""
set from = "username@gmail.com"
set realname = "Name"


# Change the following line to a different editor you prefer.
set editor = "nano"

# Basic config, you can leave this as is
set folder = "imaps://imap.gmail.com:993"
set spoolfile = "+INBOX"
set imap_check_subscribed
set hostname = gmail.com
set mail_check = 120
set timeout = 300
set imap_keepalive = 300
set postponed = "+[GMail]/Drafts"
set record = "+[GMail]/Sent Mail"
set header_cache=~/.mutt/cache/headers
set message_cachedir=~/.mutt/cache/bodies
set certificate_file=~/.mutt/certificates
set move = no
set include
set sort = 'threads'
set sort_aux = 'reverse-last-date-received'
set auto_tag = yes
ignore "Authentication-Results:"
ignore "DomainKey-Signature:"
ignore "DKIM-Signature:"
hdr_order Date From To Cc
alternative_order text/plain text/html *
auto_view text/html
bind editor <Tab> complete-query
bind editor ^T complete
bind editor <space> noop 

# Gmail-style keyboard shortcuts
macro index,pager y "<enter-command>unset trash\n <delete-message>" "Gmail archive message"
macro index,pager d "<enter-command>set trash=\"imaps://imap.googlemail.com/[GMail]/Bin\"\n <delete-message>" "Gmail delete message"
macro index,pager gi "<change-folder>=INBOX<enter>" "Go to inbox"
macro index,pager ga "<change-folder>=[Gmail]/All Mail<enter>" "Go to all mail"
macro index,pager gs "<change-folder>=[Gmail]/Starred<enter>" "Go to starred messages"
macro index,pager gd "<change-folder>=[Gmail]/Drafts<enter>" "Go to drafts"

#
ignore date *
unignore from subject to cc
unignore organization organisation x-mailer: x-newsreader:  x-mailing-list:
unignore posted-to:
```

---

### Post by Hippytaff on 2010-10-05
```

# A basic .muttrc for use with Gmail

# Change the following six lines to match your Gmail account details
set imap_user = "username@gmail.com"
set imap_pass = ""
set smtp_url = "smtp://username@smtp.gmail.com:587/"
set smtp_pass = ""
set from = "username@gmail.com"
set realname = "Name"


# Change the following line to a different editor you prefer.
set editor = "nano"

# Basic config, you can leave this as is
set folder = "imaps://imap.gmail.com:993"
set spoolfile = "+INBOX"
set imap_check_subscribed
set hostname = gmail.com
set mail_check = 120
set timeout = 300
set imap_keepalive = 300
set postponed = "+[GMail]/Drafts"
set record = "+[GMail]/Sent Mail"
set header_cache=~/.mutt/cache/headers
set message_cachedir=~/.mutt/cache/bodies
set certificate_file=~/.mutt/certificates
set move = no
set include
set sort = 'threads'
set sort_aux = 'reverse-last-date-received'
set auto_tag = yes
ignore "Authentication-Results:"
ignore "DomainKey-Signature:"
ignore "DKIM-Signature:"
[COLOR=red]ignore "date:"[/COLOR]
hdr_order Date From To Cc
alternative_order text/plain text/html *
auto_view text/html
bind editor <Tab> complete-query
bind editor ^T complete
bind editor <space> noop 

# Gmail-style keyboard shortcuts
macro index,pager y "<enter-command>unset trash\n <delete-message>" "Gmail archive message"
macro index,pager d "<enter-command>set trash=\"imaps://imap.googlemail.com/[GMail]/Bin\"\n <delete-message>" "Gmail delete message"
macro index,pager gi "<change-folder>=INBOX<enter>" "Go to inbox"
macro index,pager ga "<change-folder>=[Gmail]/All Mail<enter>" "Go to all mail"
macro index,pager gs "<change-folder>=[Gmail]/Starred<enter>" "Go to starred messages"
macro index,pager gd "<change-folder>=[Gmail]/Drafts<enter>" "Go to drafts"

#
[COLOR=red]ignore *[/COLOR]
unignore from subject to cc
unignore organization organisation x-mailer: x-newsreader:  x-mailing-list:
unignore posted-to:

```
 
Don't know if this'll work, I'm not at home to try it but worth a punt :-) changes in red

---

### Post by karthick87 on 2010-10-05
No use,still i get the date see the attachment...

---

### Post by Hippytaff on 2010-10-05
```

 
[COLOR=red]ignore *[/COLOR] 
unignore From: Subject: To: CC:
unignore organization organisation x-mailer: x-newsreader:  x-mailing-list: unignore posted-to:


```

REvert back to your original .muttrc, put a colon after From: etc as above and take out the # above ignore*

---

### Post by jtarin on 2010-10-05
This thread has been marked as solved, so you would benefit more by opening a new "topic" about your specific problem.

---

