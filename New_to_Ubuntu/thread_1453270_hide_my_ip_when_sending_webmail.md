---
title: "hide my ip when sending webmail"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by bananaboatcoat on 2010-04-13
howsa!

how can i hide my ip address when sending webmail?



:P:guitar:

---

### Post by WitchCraft on 2010-04-13
> **bananaboatcoat said:**
> howsa!

how can i hide my ip address when sending webmail?



:P:guitar:

And why would you do that ?
I suppose you're not a Chinese dissident ;-))

Anyway, first write an application that sends POP emails via telnet.
Then rewrite the application that is spoofs a different IP, and send yourself an email for testing purposes, and watch the sender IP.
(telnet works connectionless, you just don't know whether the email was actually sent)

There's no way to send an anonymous web email, because TCP/IP requires a connection.

Another way is to use proxychains and just switch many proxys between you and the webmail site. But it doesn't really hide your IP, it just makes tracking the sender more difficult.

---

### Post by bananaboatcoat on 2010-04-13
for privacy when sending one email. with all other emails sent, no worries about showing real ip. but for one email, privacy is preferred.

---

### Post by bananaboatcoat on 2010-04-13
> **WitchCraft said:**
> 

Anyway, first write an application that sends POP emails via telnet.
Then rewrite the application that is spoofs a different IP, and send yourself an email for testing purposes, and watch the sender IP.
(telnet works connectionless, you just don't know whether the email was actually sent)

There's no way to send an anonymous web email, because TCP/IP requires a connection.



i'm a noob. no programming skills in my bonez. is there an application already written?

Update: i'm a COMPLETE noob. (-= 
Update 2: i'm a noob that can copy commands you give into my command line window. /-)

---

### Post by WitchCraft on 2010-04-13
> **bananaboatcoat said:**
> i'm a noob. no programming skills in my bonez. is there an application already written?

I think I once had one called *EU*thanasia.

---

### Post by bananaboatcoat on 2010-04-13
quick google search doesn't seem to bring up anything relevant for *eu*thanasia telnet.

---

### Post by bananaboatcoat on 2010-04-13
I do not mind creating a new webmail account with a webmail service that provide IP privacy, but we wouldn't want the recipient to me struck by the fact that i'm using a webmail service that is used by superprivate emailers (e.g. hushmail). so if you know of a webmail service that doesn't have the reputation that hushmail does, but has IP privacy, just like hushmail, don't be hush with your response. :P

---

### Post by cariboo on 2010-04-13
How about [10 Minute Mail]("http://10minutemail.com/10MinuteMail/index.html")?

---

