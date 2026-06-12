---
title: "GUI to access mail (not email)"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-09-25
Some applications, notably *cron*, send mail to the system. (This has nothing to do with email.)

I find the *mail* program confusing.

I was wondering if anyone knows of an easier GUI to access the system's mail?

---

### Post by Liolikas on 2009-09-25
mail is just very old still used email program.
You have Linux means you have mail box username@system_name maybe it is not possible to use on internet but still it is email. So means you can use any mail program.

---

### Post by Paddy Landau on 2009-09-25
Thanks for the clarification, Liolikas.

So, if I'm to use my usual email client (Thunderbird), I need to know some things.

[LIST]
[*]You say that the email address is username@system_name. I know my username, but how do I find the system_name? Is that the name shown on System > Administration > System Monitor > System?
[*]Do I choose POP or IMAP for the incoming mail server?
[*]Do I use localhost as the incoming mail server? What port do I use?
[*]What do I use as my SMTP or outgoing server?
[/LIST]
I've tried various combinations but, so far, I've had no luck.

TIA

---

### Post by Liolikas on 2009-09-25
, but how do I find the system_name?
uname -n


Most simple way:
echo "myfavoritemail@zz.abudabi" > .forward

---

### Post by Mad Hacker on 2009-09-25
if you're just using it for local mail, i suggest mutt

---

### Post by ddrichardson on 2009-09-25
This has come up before - [http://ubuntuforums.org/showthread.php?t=198768](http://ubuntuforums.org/showthread.php?t=198768)

---

### Post by Paddy Landau on 2009-09-25
> **Liolikas said:**
> but how do I find the system_name?
uname -n
Thanks! It is the same as on System Monitor.

> **Mad Hacker said:**
> if you're just using it for local mail, i suggest mutt
That's almost perfect; thanks for the recommendation. I'll use that. I notice that it's recommended to install mutt-patched as well as mutt.

> **ddrichardson said:**
> This has come up before - [http://ubuntuforums.org/showthread.php?t=198768](http://ubuntuforums.org/showthread.php?t=198768)
Hmm, not quite the same, but interesting.

Thank you everyone.

---

