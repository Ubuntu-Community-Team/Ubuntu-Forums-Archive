---
title: "Evolution not wanting to send email"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by GeordieJedi on 2009-02-09
Hi all, I have a little bit of a prob with evolution. And I was hoping I could get some
help with.

I have a Gmail account, which I use for my main email correspondance.
I recently installed the LXF version of Ubuntu 8.10.
(A version from the British mag called "Linux Format or LXF")

I ran evolution for the first time used the set-up assistant. and provided the relevant
details for using evolution as my mail client (with the added bonus of using it as a
backup of my mails).

Everything seemed to go well. Evo conncted, downloaded all my mails. and I was cooking
with gas.

However today, when I either try to send any mails from Evo, or use the send/receive
button to check for any more mails to download I get the following error message =

"SSL Certificate check for imap.gmail.com:

Issuer:            E=premium-server@thawte.com,CN=Thawte Premium Server CA,OU=Certification Services Division,O=Thawte Consulting cc,L=Cape Town,ST=Western Cape,C=ZA
Subject:           CN=smtp.gmail.com,O=Google Inc,L=Mountain View,ST=California,C=US
Fingerprint:       f1:d3:de:59:9d:9c:e2:31:ea:aa:2c:a0:fc:ad:9a:61
Signature:         BAD

Do you wish to accept?"


I've done a couple of quick web searches and I come up cold.

Does anyone have any ideas? Any help or advice would be greatly appreciated.

---

### Post by physeetcosmo on 2009-02-10
> **GeordieJedi said:**
> 
However today, when I either try to send any mails from Evo, or use the send/receive
button to check for any more mails to download I get the following error message =

"SSL Certificate check for imap.gmail.com:

Issuer:            E=premium-server@thawte.com,CN=Thawte Premium Server CA,OU=Certification Services Division,O=Thawte Consulting cc,L=Cape Town,ST=Western Cape,C=ZA
Subject:           CN=smtp.gmail.com,O=Google Inc,L=Mountain View,ST=California,C=US
Fingerprint:       f1:d3:de:59:9d:9c:e2:31:ea:aa:2c:a0:fc:ad:9a:61
Signature:         BAD

Do you wish to accept?"


I've done a couple of quick web searches and I come up cold.

Does anyone have any ideas? Any help or advice would be greatly appreciated.

Hello,

When you first setup the client, did you actually try to SEND any emails?

I had issues sending when i first setup (which is the smtp protocol). I found a link in which you must setup your send mail as such:

Server Configuration:
smtp.gmail.com:587

Security:
TLS

Authentication:
PLAIN

I had my authentication set to 'Login' which requires a different protocol that Evolution doesn't support. It sounds like yours might be set to the same, of CRAM-MD5 which I believe is a certificate.

Go to: Edit >> Preferences and select your email account and click Edit. go to 'Sending eMail' tab and make sure your settings are as such.

Let me know if this works! :)

-DB

---

### Post by johnjohn2 on 2009-02-10
Try thunderbird works like an absolute champ

---

### Post by dca on 2009-02-10
If you're in someone else's network it could be a port 25 issue where you may need to change it in your email client to 587...  IOW they may have an SMTP server and you're trying to contact your own...

---

### Post by capnthommo on 2009-02-10
hi Geordiejedi.  
when i set mine up (particularly when i added a second gmail account to it - last night, as it happens) that i entered one of the account name/server as ****@gmail.com and it didn't send either but when i edited this to read as **@googlemail.com it worked just fine.  so i suspect (at least on my setup) that it is important how you term it.  it becomes so easy to just use gmail.com usually - have you inadvertently done the same as me when you set up evolution?
just a thought.
best of luck
nigel

---

### Post by GeordieJedi on 2009-02-11
Hi all, and thanks very much for the replies.

@ physeetcosmo
No, I didn't't try to send any mail from Evo when I first set it up.
I just let Evo do its thing and download all my mail off the servers.


OK, I've deleted my account within Evo, & I'll reset it up again.
If I then just type what I see as I progress, Maybe someone can point
out where I'm going wrong.

OK here goes.

Page 1
_Identity_

name = John
e-mail address = [email]Johnsmith@gmail.com[/email]


Page 2
_Receiving mail_

Server type = ??
(I originally set this up as SMTP. But In all the walkthroughs I've
read, they start with pop.

I have pop enabled on Gmail as well as IMAP. I'd rather use IMAP as I
use different PC's to check my mail, and via my phone too. & I'd like
gmail to keep the main copy of the mails on it's servers).

Security = SSL
Authentication = Password? (I don't have the option to choose plain as
otherwise suggested.


Page 3
_Receiving options_

I don't really touch the options on this page, other than to leave the
messages on the server.


Page 4
_Sending mail_

Server type = SMTP
Server = smtp.gmail.com
Security = SSL

Authentication =
Type = PLAIN
Username = [email]johnsmith@gmail.com[/email]

Remember password = (do I tick this box? Or is it not necessary If
you use plain authentication?).

And that's about it.


So if I use these options, will I get a trouble free Evo experience?
Thanks very much to all who've responded so far. And any other advice
given. This is the main reason I love Ubuntu so much. The helpfull
peeps on the forums.

---

### Post by capnthommo on 2009-02-11
hi again.
when i set up i went to the settings tab on upper right side of gmail (you said you were using gmail didn't you?)  and locate the forwarding and pop/imap section and select enable imap then open the configuration section thus
```
1. Status:  IMAP is enabled
	Enable IMAP
	Disable IMAP

2. Configure your email client (e.g. Outlook, Thunderbird, iPhone)
Configuration instructions
```
then under 
'mail clients'
select the last one on the list -    'other' 
and then work through the sections as you configure evolution (or indeed, thunderbird).
just bear in mind what i said about gmail/googlemail and the apparent need to get it right.
that worked fine for me.  basically it tells you what to enter in evolution to make it work
good luck
nigel

---

