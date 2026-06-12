---
title: "Evolution Mail Configuration Problem"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by Xalltar on 2011-04-24
Hi !

I've installed Ubuntu yesterday and I still experience some problems I can't solve by myself ... doesn't work.
I'm actually on the Evolution Mail Configuration Problem ...

I've followed the tutorial on how to configure it but i've a problem that is

"Host lookup failed:smtp.live.com: Name or service not known" when I click on Send/Receive ...

Erf ....

Any clue ?

Thanks !

---

### Post by dnairb on 2011-04-24
IIRC you need to use:

```
smtp.live.com:25
```

or, if the above doesn't work:

```
smtp.live.com:587
```

---

### Post by Xalltar on 2011-04-24
Erf ... Just tried it ... and still the same problem ....

---

### Post by dnairb on 2011-04-24
Is the same error reported?

---

### Post by Xalltar on 2011-04-24
Mh ... that's odd. At first yeah but I then rebooted and now it doesn't make this error again.

It says now : "Could not connect to smtp.live.com : connection refused" and asks for a password for the pop3 server on my mail adress ....

Well i can't send anything now due to the connection refused for smtp server ...

---

### Post by dnairb on 2011-04-24
Did you enter your password? (for your mail account)

What was the tutorial you followed? And how did you set your configuration?

---

### Post by Xalltar on 2011-04-24
Yep, i've followed indications on the web about configuring that.

[https://help.ubuntu.com/community/UsingGmailWithEvolution](https://help.ubuntu.com/community/UsingGmailWithEvolution) adapted to hotmail ...

Okay let me give you everything about my configuration :

Account Information : [EMAIL="xxxx@hotmail.fr"]xxxx@hotmail.fr[/EMAIL]
Full Name : Xaltar
Email Adress : [EMAIL="xxxx@hotmail.fr"]xxxx@hotmail.fr[/EMAIL]

Receiving mail : Server Type : POP
Server : pop3.live.com:995
Username : [EMAIL="xxxx@hotmail.fr"]xxxx@hotmail.fr[/EMAIL]
SSL Encryption

Auth Type : Password

Sending Mail : Server Type : SMTP
Server : smtp.live.com:587
TLS Encryption

Auth. Type : PLAIN
Username : [EMAIL="xxxx@hotmail.com"]xxxx@hotmail.com[/EMAIL]

I hope it can be useful for you ...

---

### Post by dnairb on 2011-04-24
That all looks OK to me. Just to confirm, look at [https://help.ubuntu.com/community/UsingHotmailWithEvolution](https://help.ubuntu.com/community/UsingHotmailWithEvolution) which is specifically for Hotmail/Windows Live Mail.

You could try 

```
Server : smtp.live.com:25
```

if you hadn't already tried that, or changing the encryption (even to No Encryption if necessary).

---

### Post by Xalltar on 2011-04-24
Hey ! I've got something new

Port 25  for SMTP seems a good thing.

The problem is nearly solved man !

I just got a Authentification Problem, SMTP keeps asking for a password even if it's okay (i've typed it a dozen times) I use my mail account password (what else should i use ?)

I got :

Aunable to authenticate to SMTP Server
AUTH command failed : Connection Reset by Peer

Please enter password blablab aaa ...

Okay gives me the same thing again and again even with a good pass (i'm sure of it)

---

### Post by dnairb on 2011-04-24
OK, progress.

Check your password carefully. If it is correct, it may just be an issue with Live's servers - give it time and try again later.

---

### Post by Xalltar on 2011-04-24
Gnnnaaaa i can connect to hotmail when i go on hotmail.fr but not in the Evolution system mail.

Okay i've typed my pass in a ten-second move (ourfff) ...

I'll try later.

I'll check you out

---

### Post by Xalltar on 2011-04-24
YAAAAAA !!!

I've found it : I made a mistake :)
In auth conf for sending email (smtp) I wrote .com instead of .fr in the box.

That's why it couldn't reach it ...

Man, thx for your help !

I can now post on that dual screen problem and I hope i'll find someone as good as you :)

Thanks again !

[Sorry for Double Post BTW I couldn't edit :) ]

---

