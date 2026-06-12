---
title: "Blackberry sending duplicate emails"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by tazz4vr on 2009-04-24
Question, I am receiving duplicate emails from a client that uses his blackberry.  Wouldn't bother me to much if only one or two, however my inbox is over run with them right now.... I am talking like 20 of the same email!

This just started happening today.  Any suggestions, aside from notifying sender, which I already have and received 20 'sorry' emails, lol....

Not sure if info helps, but emails are coming from Telus Mobility Network.

---

### Post by cmnorton on 2009-04-26
Are these ordinary emails? Do these have any error notifications, like an additional header indicating a bounce?

I ask, because a few years ago, our town's email server was swamped with Blackberry emails, because attachments were too large to go through the Blackberry's provider's network. An error would go back to the Blackberry email server, but the Blackberry's email account had been set up to forward to the user's email address on the town's email server. Then, that email failed, which caused another error message to go back to the Blackberry, which got forwarded to the town, ...

In my somewhat dubious expert opinion, this isn't Ella; it's Memorex. (The problem is on the Blackberry side.) You could always notify the administrator of their network, too.

Good luck.

---

### Post by llamabr on 2009-04-26
Look at the headers, and see whether they're bouncing, or dupliciates.  In either case, it's probably blackberry's fault.

A procmail recipe could save you from receiving duplicate emails.  I know it's taboo to suggest man pages here, but you find good recipes in man procmailrc and procmailex

---

### Post by tazz4vr on 2009-04-26
Thanks for the reply.  Upon checking the full headers, there is nothing that specifies an error.  But just in case, will it state 'error' somewhere in the header, or would I be looking for all info duplication?

---

### Post by LowSky on 2009-04-26
What has this have to do with Ubuntu, or absolute beginers?

If you have an isue with your phone, call your provider, or check with blackberry on the error.

---

### Post by tazz4vr on 2009-04-26
Considering that this is not my blackberry and when provided them with info they said they couldnt assist me.  Also because it is not generating an error message known to me, I am not sure if its is my email client having a glitch.  And since most of the people I deal with here on ubuntu are pretty cool, they usually don't mind helping out someone such as myself who is unsure what area a specific problem may fall under, and usually give me redirection on finding the right solution, whether ubuntu related or not.

---

### Post by cmnorton on 2009-04-26
I don't know if Evolution filters allow counting the number of messages in a folder, or if Evolution has a macro language. Thats all you can do, if you want to handle it at your end.

---

### Post by tazz4vr on 2009-04-26
I think the problem has been solved.  He updated something, somewhere and now the emails are arriving as normal.  I have sent an email asking how the matter was resolved, once he replies I will post info.

Thank you all for the suggestions.

---

### Post by hansdown on 2009-04-26
Please keep us posted tazz4vr.

I'd be interested to know.

It almost certainly is a blackberry problem.

[http://www.google.ca/search?q=blackberry+duplicate+email&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=blackberry+duplicate+email&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by llamabr on 2009-04-26
> **LowSky said:**
> What has this have to do with Ubuntu, or absolute beginers?

If you have an isue with your phone, call your provider, or check with blackberry on the error.

Strikes me that an absolute beginner isn't sure it's not his mail server wonking out, or a blackberry sending multiple messages, has a legitimate right to ask about it here, without being harassed about it.

Wouldn't you agree?

---

### Post by tazz4vr on 2009-04-26
Will definitely keep you informed.  Unfortunately he is on the road right now, so will probably hear back either late tonight or tomorrow sometime, but will keep you informed.

---

### Post by tazz4vr on 2009-04-26
> **llamabr said:**
> Strikes me that an absolute beginner isn't sure it's not his mail server wonking out, or a blackberry sending multiple messages, has a legitimate right to ask about it here, without being harassed about it.

Wouldn't you agree?

I do highly agree...however as I have learned not to take things too personally, I chalked it up to someone needing a nap.  Regardless of that, everyone else has been quite understanding and helpful.

---

### Post by bapoumba on 2009-04-27
> **tazz4vr said:**
> I do highly agree...however as I have learned not to take things too personally, I chalked it up to someone needing a nap.  Regardless of that, everyone else has been quite understanding and helpful.
Thanks much :)

---

### Post by tazz4vr on 2009-04-27
anytime.

---

### Post by tazz4vr on 2009-04-29
Okay, I finally heard from the client.... mind you he is a singer, not a tech guy, but this is the solution he used and so far it is working.  Also, I need to mention that he did send a request for assistance to the blackberry provider people, and has yet to be contacted.

'I shut off all my connections in the manage my connection icon and then restarted them 10 min later, not a very technical solution, I know, but seems to have worked.'

---

### Post by hansdown on 2009-04-29
Thanks tazz4vr.

Keep us posted.

---

### Post by tazz4vr on 2009-05-16
Well, so far so good, it is still working, no dup's.

---

### Post by hansdown on 2009-05-16
Good job tazz4vr.

---

