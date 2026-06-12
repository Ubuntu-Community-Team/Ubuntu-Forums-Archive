---
title: "problems connecting to mail.comcast.net"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by RebeccaHowarth on 2008-12-20
Hi,

I can send emails through Evolution ok, but in receiving them I get an error message which says I can't connect to the server.  I'd really appreciate any helpful hints.  Thanks in advance!

---

### Post by SunnyRabbiera on 2008-12-20
I personally would ditch evolution and use thunderbird if I were you, I never liked that app.
as for comcast, it could be a comcast error (I could check as I use comcast myself)

---

### Post by abn91c on 2008-12-20
comcast upgrade the  servers it is now pop3.comcast.net and smtp.comcast.net

---

### Post by SunnyRabbiera on 2008-12-20
> **abn91c said:**
> comcast upgrade the  servers it is now pop3.mail.comcast.net and smtp.comcast.net

Not for me, though I am using thunderbird.

---

### Post by RebeccaHowarth on 2008-12-20
Thanks so much for the help.  How do I change my server to pop3.mail.comcast.net?  I looked around for where to make the change, but didn't have any luck.  If that doesn't work, I'll try Thunderbird, which I may have to ask you more questions about, so I apologize in advance for any annoyance!  In any event, I really appreciate your help.

---

### Post by albinootje on 2008-12-20
> **RebeccaHowarth said:**
> Thanks so much for the help.  How do I change my server to pop3.mail.comcast.net?  I looked around for where to make the change, but didn't have any luck.  

In Evolution -> Edit -> Preferences -> Edit mail-accounts
> 
If that doesn't work, I'll try Thunderbird, which I may have to ask you more questions about, so I apologize in advance for any annoyance!  In any event, I really appreciate your help.

I also never liked Evolution, although the little calendar is OK.
Thunderbird is pretty nice.

---

### Post by RebeccaHowarth on 2008-12-20
Ok, I switched to pop3.mail.comcast.net, and I still can't recieve mail.  Here's the error message I get:

Host lookup failed:  pop3.mail.comcast.net: Name or service not known

So I'm guessing pop3.mail.comcast.net isn't my server.  I don't know anything about Thunderbird.  I'd like to give Evolution a bit more of a try.  I'll have to comcast to figure out if the problem is on their end.  Are there any other solutions I could try?  Thanks again, everyone.

---

### Post by abn91c on 2008-12-20
> **RebeccaHowarth said:**
> Thanks so much for the help.  How do I change my server to pop3.mail.comcast.net?  I looked around for where to make the change, but didn't have any luck.  If that doesn't work, I'll try Thunderbird, which I may have to ask you more questions about, so I apologize in advance for any annoyance!  In any event, I really appreciate your help.

pop3.comcast.net  to receive mail
smtp.comcast.net  to send mail

by the way kmail will run in ubuntu 8.10, that is what I use

---

### Post by RebeccaHowarth on 2008-12-20
> **abn91c said:**
> pop3.comcast.net  to receive mail
smtp.comcast.net  to send mail

by the way kmail will run in ubuntu 8.10, that is what I use

Yeah, that's the server configuration I tried.  No luck.  I really would like to see if I could solve this problem.  I'm not giving up on Evolution yet. :)

---

### Post by Kellemora on 2008-12-20
Hi RH

Possibly you have some other settings not right to receive mail.

I use mail.comcast.net and it works fine for inbound e-mails.

You have to have your UserName set.  This is NOT your whole e-mail address, just your username.  Authentication set to Passwords.  And on mine I also have 'If Available STARTTLS' as the option there.

TTUL
Gary

---

### Post by RebeccaHowarth on 2008-12-20
> **Kellemora said:**
> Hi RH

Possibly you have some other settings not right to receive mail.

I use mail.comcast.net and it works fine for inbound e-mails.

You have to have your UserName set.  This is NOT your whole e-mail address, just your username.  Authentication set to Passwords.  And on mine I also have 'If Available STARTTLS' as the option there.

TTUL
Gary

Ok, so I set my UserName as you advised.  I don't have 'If Available STARTTLS' as an option under "Password" or "Check for Supported Types."  When I click "Check for Supported Types" a small window flashes up for a fraction of a second, but it's too quick for me to read.  I can see a white x in a red box though, so that can't be good.  I still can't receive mail.

Thanks again for the assistance.

---

### Post by abn91c on 2008-12-20
look for a setting like "my server requires authentication" in the sending mail setup, that's where you need to put just your username and password

---

### Post by RebeccaHowarth on 2008-12-20
Ok, I appear to have solved this problem, but I'm not sure how.  Something about the user name, evidently, but I'm not sure what.

---

### Post by RebeccaHowarth on 2008-12-20
Oh, and before I forget:  how do I mark this thread "SOLVED"

?

---

