---
title: "problem sendig mail in thunderbird"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by capnthommo on 2009-03-25
hi everybody.  this actually started a week ago when i found that evolution, which had worked fine for my 2 gmail accounts, suddenly started refusing to send or receive mail.  i eventually installed thunderbird instead which has worked fine (if a little basically for my needs) for both accounts so far.
today one and then the other gmail account began refusing to send.  what happens is i try to send mail and get a pop-up stating  > connecting to smtp.googlemail.  this just rolls on for ages with no change.  both accounts still receive fine.  i have tried playing with the account, server settings and ssl/tls etc but no result.
i can send to and from both directly from gmail, the problem is only when i try to use t'bird
i also tried re-setting up evolution but that doesn't seem to want to play either - will also receive but not send although the result panel says 100% done (i really prefer evo but will go with whatever i can get working.
and i have definitely made no changes to the settings of t'bird prior to the problem.
i have to sleep now but if you have any suggestions/want any further info let me know and i will post in the morning.
thanks for any help you can give
cheers
nigel

---

### Post by halitech on 2009-03-25
> **capnthommo said:**
> hi everybody.  this actually started a week ago when i found that evolution, which had worked fine for my 2 gmail accounts, suddenly started refusing to send or receive mail.  i eventually installed thunderbird instead which has worked fine (if a little basically for my needs) for both accounts so far.
today one and then the other gmail account began refusing to send.  what happens is i try to send mail and get a pop-up stating    this just rolls on for ages with no change.  both accounts still receive fine.  i have tried playing with the account, server settings and ssl/tls etc but no result.
i can send to and from both directly from gmail, the problem is only when i try to use t'bird
i also tried re-setting up evolution but that doesn't seem to want to play either - will also receive but not send although the result panel says 100% done (i really prefer evo but will go with whatever i can get working.
and i have definitely made no changes to the settings of t'bird prior to the problem.
i have to sleep now but if you have any suggestions/want any further info let me know and i will post in the morning.
thanks for any help you can give
cheers
nigel

are you sure it says
[color="red"]connecting to smtp.googlemail. [/color]

first thing I would check would be router settings to make sure port 465 isn't blocked then I would check with your ISP and make sure they haven;t blocked it on their end.

Here's some info on their settings
[http://mail.google.com/support/bin/answer.py?hl=en&answer=13287](http://mail.google.com/support/bin/answer.py?hl=en&answer=13287)

edit: just looked and it should be [color="red"]smtp.gmail.com[/color] for the outgoing server.

---

### Post by oldsoundguy on 2009-03-25
Open up Thunderbird
select edit
account settings
select outgoing server
make sure the information is correct there to include the correct port. (some outfits are blocking port 25 now to reduce the spam coming from their server.)  I would call the 800 number and verify what port is the GOOD one (Comcast offers 527 as an alternate, for instance.)

---

### Post by mkvnmtr on 2009-03-25
I have never had a problem with my gmail in Thunderbird but I think I read somewhere that some people were having trouble with gmail. I think it depended on where their servers are. I think it was on slashdot that I read that. Maybe your problem is not with Thunderbird if Evolution won't work either.

---

### Post by halitech on 2009-03-25
I hadn't heard that but I'm thinking if both arent working either a) port has been blocked or b) he's got the wrong address in both.

---

### Post by capnthommo on 2009-03-26
:)  hi all.  it seems to be okay now.  halitech, i changed my outgoing server to gmail as your edit noted and that appears to have been the problem.
odd really, something must have changed at the google end as i followed their config instructions and hadn't changed a thing since then and it had worked fine thus far.  i suspect they altered their server in the uk to gmail from googlemail sometime yesterday - does that sound plausible?
thanks for the usual quick responses people.
cheers
nigel
p.s halitech, with the Bluenose avatar and the name etc you just *have* to be Halifax based.  i haven't visited for a couple of years now, but how are things there?

---

### Post by halitech on 2009-03-26
> **capnthommo said:**
> :)  hi all.  it seems to be okay now.  halitech, i changed my outgoing server to gmail as your edit noted and that appears to have been the problem.
odd really, something must have changed at the google end as i followed their config instructions and hadn't changed a thing since then and it had worked fine thus far.  i suspect they altered their server in the uk to gmail from googlemail sometime yesterday - does that sound plausible?
thanks for the usual quick responses people.
cheers
nigel

it's possible that they may have made changes on thier end in the last day or 2 and thus caused the issue you were having. Glad to hear its working now for you :) 

> p.s halitech, with the Bluenose avatar and the name etc you just *have* to be Halifax based.  i haven't visited for a couple of years now, but how are things there?

you nailed it :) been living in NS for 30 years and Halifax for the last 5. Things are okay considering the economy but guess thats a concern everywhere these days.

---

### Post by golem1989 on 2009-04-13
it doesnt work for me :/
got the same problem... but it works when im using windows, same settings, same tool (thunderbird)
but i cant send mails via stmp :/

---

### Post by halitech on 2009-04-13
what does thunderbird have for the outgoing mail server?

---

### Post by golem1989 on 2009-04-14
smtp.gmail.com:587

*********@gmail.com

TLS

---

### Post by halitech on 2009-04-14
what kind of error message does it give you?

---

### Post by golem1989 on 2009-04-14
delivering mail... waiting some minutes and then:

sending of message failed.
the message could not be sent because connecting to smtp server smtp.gmail.com failed. the server may be unavailable or is refusing smtp connections. please verify that your smtp server setting is correct and try again, or else contact your network administrator.

---

### Post by halitech on 2009-04-14
open up a terminal and type in
```
telnet smtp.gmail.com 587
```
you should get a response like this

> daryl@debian-desktop:~$ telnet smtp.gmail.com 587
Trying 209.85.147.109...
Connected to gmail-smtp-msa.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP k35sm7526182waf.54

if that fails, your ISP is blocking port 587 so try it with port 465. if that fails as well, you will need to use your ISP's outgoing mail server to send mail.

---

### Post by golem1989 on 2009-04-14
patrick@golem:~$ telnet smtp.gmail.com 587
Trying 209.85.135.111...
Connected to gmail-smtp-msa.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP e8sm13690628muf.48

---

### Post by halitech on 2009-04-14
ok, well obviously no issues there with the connection. maybe try removing the outgoing mail server and readding it

---

### Post by golem1989 on 2009-04-14
tried very often... again and again...

---

### Post by halitech on 2009-04-14
if you set it up in Evolution, does it work okay there?

---

### Post by golem1989 on 2009-04-14
nope ;>
that's why i tried thunderbird...

edit: maybe my linux cant handle smtp...? what to do about that?

---

