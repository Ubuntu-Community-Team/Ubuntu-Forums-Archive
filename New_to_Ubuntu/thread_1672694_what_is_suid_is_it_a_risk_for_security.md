---
title: "what is suid? is it a risk for security?"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by lucacerone on 2011-01-21
Dear all,
I'm not new to Ubuntu,
but only recently I started performing
some administrative task on my computer.
While managing user permission and reading to
the documentation for chmod I got a bit confused
by this "suid" bit.
As far as I have read, setting suid on a file,like a shell script
for example, allows the file to run with super-user privileges,
without actually asking for the password.

It seems a bit strange to me, so I think I probably misunderstood
what suid is and when it should be set.

Can somebody help me?

Cheers, -Luca

---

### Post by matt_symes on 2011-01-21
Hi

Does this help ?

[http://en.wikipedia.org/wiki/Setuid](http://en.wikipedia.org/wiki/Setuid)

Kind regards

---

### Post by Frogs Hair on 2011-01-21
Do you mean sudo ? Sudo is a command that allows a user to become a super user for tasks , such as installing software , in other words .a temporary elevated permission.

---

### Post by lotus@terminal on 2011-01-21
Hey Luca

This is how I understand 'SUID', when a program runs under Linux, it inherits the permissions of the    user who is running it, so if I run a program under my user account, the program    runs with the same permissions that I would have assigned to my user account. 

So,    if I cannot open a certain file and the program I am running also cannot open the    file in question, then either the program or I do not have the required permissions. If I set the SUID or SGID bit for a file, this causes any persons or  processes that run the file to have access to system resources as though  they are the owner of the file.

Hope this answers your question. :)

---

