---
title: "Mail checker for Ubuntu"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by Malfet on 2008-04-01
I'm looking for small Linux application to check and notify about new pop3-mails with possibility to remove messages directly from the server. Browsing the Net I've found KShowMail for KDE, but it didn't work out in Ubuntu with GNOME. Does anyone knows software for this task?

---

### Post by rlangset on 2008-04-01
I think maybe mailfilter available from synaptic packet manager, at least on my Linux Mint installation, is what you are looking for?
[I]Mailfilter is very flexible utility for UNIX (-like) operating systems to get
rid of unwanted e-mail messages, before having to go through the trouble of
downloading them to the local computer. It offers support for one or many
POP3 accounts and is especially useful for dialup connections via modem,
ISDN, etc. Install Mailfilter if you'd like to remove spam from your POP3 mail
accounts.

With Mailfilter you can define your own filters (rules) to determine
which e-mails should be delivered and which are considered waste. Rules
are Regular Expressions, so you can make use of familiar options from
other mail delivery programs such as e.g. procmail.

If you do not get your mail from a POP3-Server you don't need Mailfilter.[/I]


Another one is pop3browser:

[I]pop3browser is intended to delete unwanted (SPAM) mails before downloading
via a low-bandwidth connection.[/I]

Otherwise Thunderbird got some spamfilter possibilitys.

---

### Post by Malfet on 2008-04-02
Thanks a lot, but I don't want a software to filter my messages. Just want to be informed about new messages and sort them by myself. That's so essential, so obvious and so easy task! There are utility to do it with Gmail account, but not for ordinary common pop3 mail box. Extremely strange... How do people survive without it???
Except, these programs even do not have a GUI.

---

### Post by rlangset on 2008-04-02
Have you looked at [www.mail2web.com?](www.mail2web.com?)

---

### Post by kextyn on 2008-04-02
> **Malfet said:**
> Thanks a lot, but I don't want a software to filter my messages. Just want to be informed about new messages and sort them by myself. That's so essential, so obvious and so easy task! There are utility to do it with Gmail account, but not for ordinary common pop3 mail box. Extremely strange... How do people survive without it???
Except, these programs even do not have a GUI.

You could set up a redirect to send your pop3 mail to a gmail account.  I currently have my server set to check 3 yahoo addresses, 2 of my own pop3 addresses, as well as 3 catchall accounts (*@domain.com) and redirects them all to an address of my choosing.  It even keeps the To field intact so that if I check it in gmail it shows that it was sent to [email]user@yahoo.com[/email] instead of gmail.

If you're interested I used this guide to set it up (I just ignored most of the stuff at the bottom, just using fetchmail and procmail):
[http://www.gentoo.org/doc/en/guide-to-mutt.xml](http://www.gentoo.org/doc/en/guide-to-mutt.xml)

---

### Post by Malfet on 2008-04-02
> **kextyn said:**
> You could set up a redirect to send your pop3 mail to a gmail account.  I currently have my server set to check 3 yahoo addresses, 2 of my own pop3 addresses, as well as 3 catchall accounts (*@domain.com) 

Yea, thanks for the idea - it worked out for me! 
I've installed GMail notify and it works nicely, besides I got one more level of SPAM protection :) and can still send mails as usual through my Opera mail client.

Thanks a lot.
M.

---

