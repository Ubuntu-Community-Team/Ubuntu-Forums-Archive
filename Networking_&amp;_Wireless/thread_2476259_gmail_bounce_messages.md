---
title: "gmail bounce messages"
date: 2022-06-21
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2022-06-21
For some but not all gmail addresses I am getting email sent from our server bounced. 
[FONT=arial]We seem to get this most often from companies who have their email domain hosted at google.[/FONT]
The Message is quoted below:

```
host aspmx.l.google.com [2607:f8b0:4002:c1b::1a]
    SMTP error from remote mail server after pipelined end of data:
    550-5.7.1 [2603:3001:600:4a00::8a4d] Our system has detected that this message
    550-5.7.1 does not meet IPv6 sending guidelines regarding PTR records and
    550-5.7.1 authentication. Please review
    550-5.7.1  [https://support.google.com/mail/?p=IPv6AuthError](https://support.google.com/mail/?p=IPv6AuthError) for more information
    550 5.7.1 . p66-20020a819845000000b0031776b8e643si14447369ywg.217 - gsmtp
``` [FONT=arial]The server has a static IPv4 address and as far as I can tell there is no IPv6 address associated with it. There was supposed to be a PTR record already but I've contacted our ISP (Comcast) to verify and if necesssary fix the PTR record.
[/FONT]

---

### Post by TheFu on 2022-06-21
In the beginning of June, Google started mandating that email authentication use OAuth2. This requires getting a new token every so often (via an https request) and using that for smtp and imap authentication.  Since google did that, I stopped checking gmail. It was never important to me, so after doing the 10 minutes to discover it was related to OAuth2 mandates, I stopped bothering.

Google warned us about this change last year, then earlier this year, then multiple times in May.  I ignored them all.  I'm positive that me not checking my gmail accounts is driving them nuts. Positive.

Ok ... perhaps not.

---

### Post by rsteinmetz70112 on 2022-06-21
Thanks,

I'll look into setting that up, I don't check gmail, but unfortunately we need to email people who use gmail so I sort of need to fix it.

---

### Post by TheFu on 2022-06-21
So, I just sent an email to a gmail account from my personal email server using a "no-reply" email address.

It was accepted and dropped into the spam folder for gmail.  That should be expected.  

So, whatever is happening is just on your server.

My email SMTP server (it is an in/out gateway) ... has IPv6 disabled and I haven't setup any IPv6 DNS records of any sort, whatsoever.

The gmail transaction:
```
Jun 21 19:52:15 spam1 postfix/smtp[8845]: 8D48822B3A: to=<e0170f3de0f81efaf916b8693@gmail.com>, relay=gmail-smtp-in.l.google.com[74.125.21.26]:25, delay=0.58, delays=0/0.01/0.25/0.32, dsn=2.0.0, status=sent (250 2.0.0 OK  1655841135 x64-20020a817c43000000b0030036809153si20451657ywc.507 - gsmtp)
Jun 21 19:52:15 spam1 postfix/qmgr[841]: 8D48822B3A: removed

```
Don't know that will help or not.

I changed to gmail address to protect the guilty, but NOTHING else was modified. ;)

---

### Post by rsteinmetz70112 on 2022-06-22
I'm still having trouble, I've gotten my ISP to check the PTR record, so that shouldn't be the problem. There are no IPv6 records, unless my ISP has set them up somehow, but I can't find any evidence that they exist.

---

### Post by SeijiSensei on 2022-06-22
You can check yourself:

```
host -t ptr ip.addr.of.host
```

For instance, 

```
$ host -t ptr 185.125.188.73
73.188.125.185.in-addr.arpa domain name pointer smtp-mx-ubuntu-1.canonical.com.

```

Any mail server needs to have reverse-resolution (PTR records) configured correctly and should at a minimum be using SPF. What do you see if you use 
```
host -t txt domain.name
```

You should see a record like this:

```
$ host -t TXT  example.com
example.com descriptive text "v=spf1 a:smtp.example.com a:mail.example.com ~all"

```

Nowadays you also need to be running DKIM as well for the best chance of delivery. I run listservs and had to add DKIM signing to insure our postings would reach all the subscribers. [https://www.linuxbabe.com/mail-server/setting-up-dkim-and-spf](https://www.linuxbabe.com/mail-server/setting-up-dkim-and-spf)

---

### Post by rsteinmetz70112 on 2022-06-22
Thanks, that confirms the ptr record exists and is correct.

I think I may need to change the configuration of my email server, I'm using exim4 and it appears to default to IPv6, but you can disable IPv6, so I'm trying that. But some information I've found implies that google is looking for and IPv6. From their documentation:

[https://support.google.com/mail/answer/81126?visit_id=637915049167321565-1683936288&p=IPv6AuthError&rd=1#authentication](https://support.google.com/mail/answer/81126?visit_id=637915049167321565-1683936288&p=IPv6AuthError&rd=1#authentication)
at the bottom of which is the text
   >  Fix IPv6 authorization errors


    An IPv6 authorization error could mean the PTR record for the sending
    server isn&#8217;t using IPv6. If you use an email service provider, confirm
    they&#8217;re using an IPv6 PTR record.


    Here's an example of an IPv6 authorization error:
    550-5.7.1: Message does not meet IPv6 sending guidelines regarding PTR
    records and authentication. 


My ptr record is IPv4

---

### Post by rsteinmetz70112 on 2022-06-22
I've tweaked my settings and am waiting to see if test messages go through. 

I've now gotten another google bounce, based on replying to a email we recieved for a person we're interviewing for ajob.

> [FONT=-moz-fixed]host gmail-smtp-in.l.google.com [142.250.9.27]
    SMTP error from remote mail server after pipelined end of data:
    550-5.7.1 [50.251.172.148      12] Our system has detected that this message is
    550-5.7.1 likely unsolicited mail. To reduce the amount of spam sent to Gmail,
    550-5.7.1 this message has been blocked. Please visit
    550-5.7.1  [https://support.google.com/mail/?p=UnsolicitedMessageError](https://support.google.com/mail/?p=UnsolicitedMessageError)
    550 5.7.1  for more information. y63-20020a0def42000000b0030c377a40f6si24727682ywe.506 - gsmtp
[/FONT]


WTF?

Google advises adding a text record for the domain.

---

### Post by TheFu on 2022-06-23
I don't have DKIM, but I do have STRICT SFP records.

Something changed at gmail.  A listsrv that forwards emails for a group is having issues with gmail refusing too.  I don't know the email admin, so I cannot contact them personally, but I do know the listsrv manager and have reached out. Doubtful that person is an email admin with sufficient background to help.

---

