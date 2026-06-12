---
title: "anyone use mutt?"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by Hippytaff on 2010-10-02
when trying to send mail with mutt i get this - Can not connect to me.gmail.com connection timed out

this is my .muttrc

```

set from = "hippytaff@gmail.com"
set realname = "GARETH WILLIAMS"
set imap_user = "hippytaff@gmail.com"
set folder = "imaps://imap.gmail.com:993"
set spoolfile = "+INBOX"
set postponed ="+[Gmail]/Drafts"
set trash = "imaps://imap.gmail.com/[gmail]/Trash"
set header_cache =~/.mutt/cache/headers
set message_cachedir =~/.mutt/cache/bodies
set certificate_file =~/.mutt/certificates
set smtp_url = "smtp://hippytaff@smtp.gmail.com:578/"
set move = no #stop asking to "move read messages to mbox"!
```


any ideas? can recieve mail and connects ok! couldn't find anything on the infonet. brain hurts

---

### Post by Hippytaff on 2010-10-02
Guess I should use a mutt forum but they'll laugh at me for my lack of knowledge :-)

Mwahaha a mutt fool who knows nothing about anything mwahaaha - that's what they'll say :-)

---

### Post by oregonbob on 2010-10-02
I use mutt for sending mail and attachments from scripts. I wonder if mutt doesn't know what smtp to use? What does your mail log in /var/log/... say?

---

### Post by Hippytaff on 2010-10-02
```

Sep 30 18:23:22 ubuntu postfix/master[1091]: daemon started -- version 2.7.0, configuration /etc/postfix
Sep 30 20:03:00 ubuntu postfix/master[1091]: reload -- version 2.7.0, configuration /etc/postfix
Oct  1 18:30:02 ubuntu postfix/master[1100]: daemon started -- version 2.7.0, configuration /etc/postfix
Oct  1 18:30:44 ubuntu postfix/master[1100]: reload -- version 2.7.0, configuration /etc/postfix
Oct  1 18:30:49 ubuntu postfix/master[1100]: reload -- version 2.7.0, configuration /etc/postfix
Oct  1 20:21:01 ubuntu postfix/master[1100]: reload -- version 2.7.0, configuration /etc/postfix
Oct  2 00:35:38 ubuntu postfix/master[1027]: daemon started -- version 2.7.0, configuration /etc/postfix
Oct  2 00:36:27 ubuntu postfix/master[1027]: reload -- version 2.7.0, configuration /etc/postfix
Oct  2 09:17:57 ubuntu postfix/master[1021]: daemon started -- version 2.7.0, configuration /etc/postfix
Oct  2 09:21:49 ubuntu postfix/master[1021]: reload -- version 2.7.0, configuration /etc/postfix
Oct  2 09:34:24 ubuntu postfix/master[1021]: reload -- version 2.7.0, configuration /etc/postfix
Oct  2 12:48:16 ubuntu postfix/master[1021]: reload -- version 2.7.0, configuration /etc/postfix
Oct  2 17:15:10 ubuntu postfix/master[1017]: daemon started -- version 2.7.0, configuration /etc/postfix
Oct  2 20:06:45 ubuntu postfix/master[1017]: reload -- version 2.7.0, configuration /etc/postfix
Oct  2 20:13:30 ubuntu postfix/master[1017]: reload -- version 2.7.0, configuration /etc/postfix
Oct  2 20:13:45 ubuntu postfix/master[1017]: reload -- version 2.7.0, configuration /etc/postfix
Oct  2 20:14:54 ubuntu postfix/master[1017]: reload -- version 2.7.0, configuration /etc/postfix
Oct  2 20:15:03 ubuntu postfix/master[1017]: reload -- version 2.7.0, configuration /etc/postfix

```

---

### Post by Hippytaff on 2010-10-02
Do you think postfix needs configuring?

---

### Post by MattBD on 2010-10-02
> **Hippytaff said:**
> Do you think postfix needs configuring?

No - it's not one of mutt's dependencies.

I use a .muttrc that was mentioned on [Lifehacker a while ago]("http://lifehacker.com/5574557/how-to-use-the-fast-and-powerful-mutt-email-client-with-gmail") and it works fine, even though I also have postfix installed, so I doubt that's the problem.

You might want to replace your existing .muttrc with that one (and amend it as appropriate) and see how you get on with that.

---

### Post by Hippytaff on 2010-10-02
tried the muttrc just remains on sending meassage for ever. hence the original temeout....foxed...cheers for that though

---

### Post by spiky001 on 2010-10-02
MattBD will the same work for an AOL account? I to am try to set up a terminal email

---

### Post by Hippytaff on 2010-10-02
as far as I know any webbased email account will work, making the obvous changes :-)

---

### Post by MattBD on 2010-10-02
> **spiky001 said:**
> MattBD will the same work for an AOL account? I to am try to set up a terminal email

I expect some of it will work OK with an AOL account, but that particular .muttrc is really geared towards Gmail, so you'd have to make a few changes.

Alternatively, Gmail can fetch email from other email accounts so one possibility is setting up a new Gmail account, setting it to fetch mail from the AOL account and then using that .muttrc with the new Gmail account.

---

### Post by Hippytaff on 2010-10-02
still no idea why it won't send mail....oh well...think I've been beaten this time

---

### Post by MattBD on 2010-10-02
> **Hippytaff said:**
> still no idea why it won't send mail....oh well...think I've been beaten this time

Well, I've just had a look through your original .muttrc and compared it with my own and the only thing I can see that you need and haven't got is set imap_pass and set smtp_pass, and I assume you have those but took them out before posting them, so I can't suggest anything else, I'm afraid.

---

### Post by Hippytaff on 2010-10-02
I've taken those out, but mutt prompts for passwords without them and it was the same problem with them. nevermind, perseverance will succeed!! :-D

---

### Post by andrew.46 on 2010-10-02
Hi hippytaff,

Have you made a typo here:

```
set smtp_url = "smtp://hippytaff@smtp.gmail.com:**[COLOR="Red"]578[/COLOR]**/"
```

I believe the correct port is actually *587* :).

Andrew

---

### Post by MattBD on 2010-10-03
> **andrew.46 said:**
> Hi hippytaff,

Have you made a typo here:

```
set smtp_url = "smtp://hippytaff@smtp.gmail.com:**[COLOR="Red"]578[/COLOR]**/"
```

I believe the correct port is actually *587* :).

Andrew

Oops, I missed that when comparing them! I reckon changing that will probably solve the issue.

---

### Post by Hippytaff on 2010-10-03
I love you guys - was a typo, well spotted

---

### Post by andrew.46 on 2010-10-03
Mind you there is another option to using gmail with mutt which is to use pop3 over ssl rather than imap, this is the technique I use myself although I will admit that the new kid on the block IMAP seems to be very popular these days :(. With this one uses fetchmail or getmail to pick up the mail, procmail to receive and optionally sort the mail and then mutt to read the mail. Sending the mail is handled my something like msmtp. It is a great system and has been working for me for some years now, I could not warm to IMAP....

Andrew

---

### Post by Hippytaff on 2010-10-03
imap is easier :-)

---

