---
title: "Evolution and Gmail"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by GeordieJedi on 2009-05-09
Hi again all, hope your all well.

I've recently re-installed Ubuntu (8.10) and am in the process of
setting up all of my apps and such.

I have a couple of Quick questions Re: Evolution

1.
When entering the details for receiving email, which is
preferable? POP or IMAP. (I have both POP and SMTP enable in Gmail)
(Am I right in thinking that I can use IMAP to recieve, and STMP to
send?)

2.
Would this stop me sending/recieving email via POP from my Mobile
phone?


3.
Slightly related Issue - I backed up my mail about a month ago on a
previous install. Now when I re-installed my Gmail account a few
weeks later, and restored by back-up al went well, But when I asked
evolution to get my new email, it did. However I had a section of
about 7-10 days of mail that would not transfer from Gmail to Evo
on my hd? (EG: say from the 1st to the 10th of the month, was sitting
there looking at me on my Gmail accout [via Web mail] but wouldnt
download to my pc)


Does anyone have any ideas?

Thanks in advance for any help :D

---

### Post by Irony on 2009-05-09
POP/IMAP differences here;

[http://mail.google.com/support/bin/answer.py?answer=75725](http://mail.google.com/support/bin/answer.py?answer=75725)

Overall here;

[http://mail.google.com/support/](http://mail.google.com/support/)

---

### Post by Irony on 2009-05-09
Note that IMAP syncs both your online email with thunderbird so that for instance and email you compose and send from thunderbird also appears in your gmail account online, whereas with POP once you fire up thunderbird your emails end up in thunderbird and disappear from online.

---

### Post by ugm6hr on 2009-05-09
If you want to leave messages on the GMail server, I would recommend IMAP.  This will ensure that messages you read on Evolution will be marked as read on GMail and vice-versa.

If you download mail to your HD using Evolution and delete from GMail, POP is simpler.

---

### Post by GeordieJedi on 2009-05-10
WooHoo!

Thank you VERY much indeed, ugm6hr and Irony.

It worked like charm. (And it seemed to solve Prob No 3, I seem to
have Access  to all of my mail now :D ).

If I can be cheeky and ask another question?

I would like to make a backup copy, of all of these emails to my HD.
(So I dont have to re-download them all again every time I re-install
Ubuntu/Evolution).

How do, I achieve that?

Once again. Thank you in advance for all help and advice.
Cheers.

---

### Post by ugm6hr on 2009-05-10
Are you using IMAP or POP then?

If IMAP, the mails are never really downloaded to your HD, just retrieved when you select the header.

You can back up all settings etc by just saving the folder ~/.evolution

Just copy it back after a reinstallation.

If POP, I'm not certain, but I suspect that the emails are probably also stored in that folder (I use T-bird for POP).

---

### Post by GeordieJedi on 2009-05-10
Areet,

I'm now using IMAP to retrieve my mails.
(Sorry for the lack of an explanation...Doh!)

Im just sure I saw an option for synchronizing/backing up all my mails
to my HD whilst using IMAP?

Something about working offline. However when I slected that option,
nowt much happend.

Even though, I think that IMAP is the better option overall.
Cheers :-D

---

### Post by Irony on 2009-05-12
Just drag the emails you want saved to your local folders in thunderbird/evolution - this will put them on your hard drive (.evolution) and delete them from the email servers.

Note I think IMAP isn't really saving anything to your local drive it is simply syncing what you see in thunderbird to what is on the email servers.

---

### Post by lvleph on 2009-05-12
I don't mean to hijack this thread or down on the OP, but why would one want to lose the power of gmail by using a mail client? Heck, I use my gmail as a mail client for pop3 mail accounts I have with work. What am I missing?

---

