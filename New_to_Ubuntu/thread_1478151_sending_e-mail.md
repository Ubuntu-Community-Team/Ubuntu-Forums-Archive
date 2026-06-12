---
title: "sending e-mail"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by jackj on 2010-05-09
Hi!  I thought I had e-mail set up and working, but not so.  Receiving seems to be working just fine.  I thought sending was working, too.  

When sending, the e-mails get as far as the outbox, and there they get stuck.

I would appreciate help.  Jack

---

### Post by kimberlite on 2010-05-09
What software are you using (Thunderbird, Evolution, etc)?

---

### Post by sadaruwan12 on 2010-05-09
What kind of a email service provider you're using is it a web base like gmail or from an ISP.

If you're using an account from your local ISP then check the settings for the outgoing mail server is correct.

---

### Post by jackj on 2010-05-09
Thanks for your replies.
 
I'm using Evolution. Am using an ISP. Things may be degrading some, since I don't seem to be receiving anything at this time either.

---

### Post by kimberlite on 2010-05-10
So you have to check out your SMTP setting for outgoing mails. Ask your ISP for their setting (secure connection, port number, authentication, etc).

---

### Post by jackj on 2010-05-11
I called the ISP.  She said all my settings were correct.  Everything I send backs up in the outbox.

An e-mail I sent two days ago made it through.   Don't understand that.

I don't know what to do next.  I've fiddled with all the settings.  If anyone has any ideas, I would appreciate hearing from you.

---

### Post by lisati on 2010-05-11
With Evolution, when there's an error sending mail, a warning *sometimes* pops up. Failing that, take a look for a notification at the bottom of Evolution's main window with a yellow triangle. Clicking on the yellow triangle should show the error message.

edit (afterthought): I'm on Vista at the moment, waiting for some video to render, so I'm unable to check the available options. Is there some kind of "work offline" option or "send mail immediately" option that needs to be toggled?

---

### Post by jotto! on 2010-05-11
who is your ISP?

---

### Post by lisati on 2010-05-11
> **jotto! said:**
> who is your ISP?

Good question. I know that Yahoo sometimes puts limits on how many mails you can send in a day.

If the OP had reported emails to perfectly good email addresses getting bounced for no apparent reason, I would have suggested checking sites such as [blacklistalert.org]("http://blacklistalert.org") and [debouncer.com]("http://debouncer.com")

---

### Post by jackj on 2010-05-12
Thanks for all the replies.

I do get an error message in a little triangle at the bottom that tells me Evolution couldn't make a connection with my ISP.  The ISP is comcast, by the way.

Some things that are bothering me is Evolution is asking me for my username, and I give it my e-mail username, which only makes sense to me, although I have tried others.

It also bothers me that Evolution is asking me if I want it to remember my password, but it never asks what my password is.  I would think that comcast would require the password.

Again, thanks for your help.

---

### Post by jackj on 2010-05-12
Just a quick note.  Looks like Evolution is receiving e-mail now.  Problem only with sending.

---

### Post by jackj on 2010-05-14
Problem solved!  Thanks for all your help.:smile:

What I did was abandon Evolution and went to Thunderbird, and it was an easy install, with some help from Comcast.  Comcast supports Thunderbird, but not Evolution.

Thunderbird appears to be less sophisticated than Evolution, but it works, and I'm sure I'll get used to it.

Again, Thanks!

---

### Post by knight69 on 2010-06-10
Don't know if this is applicable in your case, but I found that outgoing mail will hang in the outbox when you have two or more email accounts set up with different outgoing servers (e.g., smtp.gmail.com for one account and smtp.yahoo.com for another account).  If you have this problem with more than one account, you can fix it by using the same outgoing server for all accounts.  (Preferably use the outgoing server for the primary (default) account. 

When you try to set up two or more accounts in Thunderbird, it will warn you against trying to set up more than one outgoing server.

---

### Post by AgentZ86 on 2010-06-12
I got the same exact problem with comcast

It's the port for comcast on outgoing mail needs to be port 587

I can easily do this with thunderbird

and when adding the smtp.comcast.net:587 for outgoing mail of evolution it does not work

I believe this is a evolution problem since thunderbird works fine when setting the outgoing mail port to 587

I don't know what else to try for evolution outgoing mail, unless there is some other way to change the outgoing port ? 

Please advise

---

