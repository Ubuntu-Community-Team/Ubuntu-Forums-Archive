---
title: "evolution is able to send from gmail acct, but not school email acct."
date: 2009-06-05
forum: New to Ubuntu
---

### Post by coober85 on 2009-06-05
Hey everyone, I have a problem I've yet to see on the forums.

I use evolution in jaunty, 
I have two accounts set up: gmail, and my student email
I can recieve emails from both just fine.
I can send emails from my gmail account just fine.
but my student email does send messages.

I tried testing the ping's on both (ping smtp.gmail.com and ping smtp.pacific.edu) and only the gmail account seems to work.

I have AT&T broadband, and I've never run into any issues with firewalls or accessibility issues.

I'm going through and trying every possible combination (required authentication checked-unchecked; SSL, TSL, no encyrp; the various authentication types) but nothing seems to be working. what should I do?

oh yeah my student receiving emails options are as follows:
POP
pop.pacific.edu
No encyrp
Password auth type
remember password

tried it on thunderbird and got the same result... "server isn't connected or is refusing connections"....

PS
I've noticed if you Check for Supported Types and it takes longer than a few seconds, your email won't work.

---

### Post by Cypher on 2009-06-05
You can use your ISP's SMTP server to send the email, you don't have to use your student account's SMTP server (assuming they give access to it). Call AT&T and ask them what the SMTP server is for you (unless you already know it)..

---

### Post by LewRockwell on 2009-06-05
[http://www.justanswer.com/questions/1kf8z-cant-connect-ts-smtp-server](http://www.justanswer.com/questions/1kf8z-cant-connect-ts-smtp-server)

might be along the lines of:  smtp.att.yahoo.com

confirm with provider

as always, your mileage may vary

---

### Post by louieb on 2009-06-05
ATT blocks the normal smtp port 25. ATT's smtp servers use port 465.  
Does your student account use port 25 for its smtp server access?

ATT will unblock port 25 but you have to request it. or you can use ATT's smtp server to send mail for all your accounts. - Probably the best thing to do.

---

