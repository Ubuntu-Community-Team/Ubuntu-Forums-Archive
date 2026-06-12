---
title: "Mail Server w/o Port 25?"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by adamjkok on 2010-10-02
Okay, here's what I wanna do (even though I know very little about this stuff):

I'd like to run a mail server for my domain. This should be accessible using something like Roundcube or Atmail. Problem is, the local ISP has the following restrictions:

[LIST]
[*]No inbound port 80 (obviously outbound is allowed or else I wouldn't be on here)
[*]No inbound or outbound port 25 *except* to *their* SMTP server (kinda dumb because it doesn't require authentication or really have any filtering)
[*]465 and 587 are allowed (less commonly-used ports but Gmail has these open)
[/LIST]
The web host I *was* using for free to do this (OrangeServe) "updated" their systems yesterday to V4.0 and one of the new "features" is adverts on *all* free websites (which messes my entire site up, not to mention that now my site simply returns a 404 error). The solution I've designed for the *website* is to pretty much forward the domain root and the www subdomain on port 80 to something like w2.<domain>.<tld>:<port> through the redirect feature provided by PointHQ.com. Unfortunately, I need to host my own email because Google Apps does not allow .TK domains and I'm not even considering M$ H*tmail (and OrangeServe just doesn't work because they broke my entire site).

Now that I'm done rambling, can someone help me design a solution for this problem (for a green user because I suck at Linux)?

---

### Post by cariboo on 2010-10-03
[Google apps?]("http://www.google.com/apps/intl/en/group/index.html") Will allow you set up an email service using your domain name.

---

### Post by adamjkok on 2010-10-03
> **cariboo907 said:**
> [Google apps?]("http://www.google.com/apps/intl/en/group/index.html") Will allow you set up an email service using your domain name.
I *explicitly* said that Google Apps blocks .TK domains because they are free. I don't know a nicer way to say this: read more carefully! A few months ago, they disabled all accounts @something.tk and new signups redirect to sorry.google.com with no captcha to override it. At least last I checked.

---

### Post by srs5694 on 2010-10-03
AFAIK, if your ISP is blocking incoming port 25, you won't be able to run a world-accessible mail server on your own local computer. Even if port 25 were unblocked, it's possible that it wouldn't work well, since many anti-spam systems block mail from or to residential accounts (which I'm guessing you've got).

Your best bet may be to go with a domain hosting provider. They host your domain (Web, e-mail, and perhaps other servers depending on your needs) on their server for a few dollars a month. Do a Web search on "domain hosting" and you'll get lots of hits. FWIW, I use [Lunarpages,](http://www.lunarpages.com) which charges $3.95 a month and up (*way* up), depending on your needs. (I've got a $6.95/month plan myself.)

One awkward feature with domain hosting is handling outgoing e-mail. Because your ISP blocks outgoing port-25 traffic, you'll have to either send outgoing e-mail through them or configure your mail clients to send on another port to your domain hosting ISP. The former option will work fine *if* your ISP doesn't insist that you use their domain name on outgoing e-mail and if recipients aren't too fussy about matching claimed domain names with server IP addresses. The latter option will work *if* the domain hosting provider offers the requisite support. Look into these details before signing up for a plan.

Another option might be to upgrade your local ISP plan. Many ISPs offer various grades of service. There may be a service grade that doesn't block those ports you want to use. My impression is that most such services cost enough that it'll be cheaper for you to use a domain hosting ISP, though.

---

