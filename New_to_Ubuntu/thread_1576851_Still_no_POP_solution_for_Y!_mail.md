---
title: "Still no POP solution for Y! mail?"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by CFury on 2010-09-17
I've searched and tried all the suggestions for both Evolution & Thunderbird, however I'm still not able to retrieve my Y! mail (free).  There's got to be a way so I'm sure I missed something.

Cheers

---

### Post by Jazzy_Jeff on 2010-09-17
I found this on a website.

Yahoo Mail offers standard POP3 access for receiving emails incoming through your Yahoo mailbox, by using your favorite email client software. To setup your email client for working with your Yahoo account, you need to select the POP3 protocol and use the following mail server settings:
Yahoo Incoming Mail Server (POP3) - pop.mail.yahoo.com (port 110)
Yahoo Outgoing Mail Server (SMTP) - smtp.mail.yahoo.com (port 25)

---

### Post by lisati on 2010-09-17
Do you mean Yahoo mail?

---

### Post by Chris1274 on 2010-09-17
I don't think you can with a free account. It's available only to paid subscribers.

---

### Post by wilee-nilee on 2010-09-18
Firefox has a addon yahoo mail notifier which will show when mail has arrived in the free account with a popup and noise if you want, and a panel icon. The cheapest yahoo mail is very low though if somebody wanted to pay for it.

---

### Post by CFury on 2010-09-18
> **Jazzy_Jeff said:**
> I found this on a website.

Yahoo Mail offers standard POP3 access for receiving emails incoming through your Yahoo mailbox, by using your favorite email client software. To setup your email client for working with your Yahoo account, you need to select the POP3 protocol and use the following mail server settings:
Yahoo Incoming Mail Server (POP3) - pop.mail.yahoo.com (port 110)
Yahoo Outgoing Mail Server (SMTP) - smtp.mail.yahoo.com (port 25)

I tried and Thunderbird connects, hangs for a while, and then times out.  I'm sure there's a way to do this with a free account.

> **lisati said:**
> Do you mean Yahoo mail?

Yes ma'am.

---

### Post by CharlesA on 2010-09-18
You need a paid account for POP3/IMAP access with Yahoo Mail.

POP3/IMAP are free for gmail tho.

---

### Post by the.phantom on 2010-09-18
might google ypops

it has worked on windows for years and if you google
"ypops for ubuntu" there appears to be a working version 

it's free

---

### Post by Legendary_Bibo on 2010-09-18
Go into your yahoo account, change the region to yahoo asia (I forget how to do this)
enable POP3 in the options (You'll have to look in the options)
Open up you mail service thingy, and because I only use evolution, my instructions will be according to evolution.

1. Go into Edit>Preferences
2. Click "Add" on Mail Accounts
3. Identity Tab
Full Name: Your actual name, or the name you used when signing up with Yahoo
E-mail: [email]whatever@yahoo.com[/email] <--Put your full e-mail address.
4.Receiving e-mail tab:
Server Type: POP
Server: plus.pop.mail.yahoo.com:995
Username: whatever <--only the first part of your e-mail without the @yahoo.com part
Use SSL encryption in Security
Authentication type is set to password, the other drop down menu is set to "Check for supported Types", and you can enable "Remember password" if you want.
5.Receiving Options Tab:
Change these setting as you desire, I just left them as the default.
6. Sending E-mail tab:
Server Type: SMTP
Server: plus.smtp.mail.yahoo.com:465
Check "Server requires authentication"
Security: SSL encryption
Authentication:
Type: PLAIN, and the dropdown menu next to it is "Check for supported types"
Username: same as the username before.
Check the "Remember password" box if you want.

I can't guarantee that Evolution will let you send your e-mail through your yahoo account. It doesn't for me, but it does for some people. That's why I have two e-mail addresses so if I reply to a yahoo message I can just select my other account in the "From" dropdown menu.

---

### Post by cmcanulty on 2010-09-18
This worked for me in hotmail and probably for yahoo also

---

### Post by CFury on 2010-09-18
LB, Looks like they've taken away the POP3 button/options after Yahoo Asia is selected.  I've read about this somewhere after trying it out myself.  It appears there's another place I can look as far as enabling POP3 forwarding, just have to do some poking about.

Cheers.

---

### Post by cmcanulty on 2010-09-19
Woops I see I left out  the link, here it is.
[http://www.dkszone.net/how-to-make-hotmail-or-livemail-as]("http://www.dkszone.net/how-to-make-hotmail-or-livemail-as")

---

### Post by philinux on 2010-09-19
Yahoo pop works in UK but you have to enable it in Options. However I was getting too many timeouts so I now divert my Yahoo mail to Hotmail and use Evolution filter. Works a treat.

---

### Post by jcolyn on 2010-09-19
> **CharlesA said:**
> You need a paid account for POP3/IMAP access with Yahoo Mail.

POP3/IMAP are free for gmail tho.

Sorry you are wrong. I get yahoo (free) mail into Kmail.

pop port setting is 995 and smtp port is 465

You also have to set SSL for security...

---

### Post by lbrty on 2010-09-20
According to wikipedia.org:
The POP3 protocol is free some countries but not others (not free in United States).

[http://en.wikipedia.org/wiki/Yahoo_mail#Features_2](http://en.wikipedia.org/wiki/Yahoo_mail#Features_2)

I use lavabit.com It is free, secure and has a great privacy policy which gmail (google) does not.

---

### Post by CharlesA on 2010-09-20
> **jcolyn said:**
> Sorry you are wrong. I get yahoo (free) mail into Kmail.

pop port setting is 995 and smtp port is 465

You also have to set SSL for security...

Meaning, you don't go thru yahoo. To go thru Yahoo you need to get a "Plus" account, at least in the US.

---

