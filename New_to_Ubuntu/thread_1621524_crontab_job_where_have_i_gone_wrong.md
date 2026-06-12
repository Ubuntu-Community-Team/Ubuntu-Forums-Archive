---
title: "crontab job where have i gone wrong"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-11-14
here is a link to a thread i had previously marked as solved

[http://ubuntuforums.org/showthread.php?t=1620745](http://ubuntuforums.org/showthread.php?t=1620745)

where have i gone wrong here is what i have entered

SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin

00 3 * * *  /sbin/shutdown -h now

tks

---

### Post by apollothethird on 2010-11-14
> **rburkartjo said:**
> here is a link to a thread i had previously marked as solved

[http://ubuntuforums.org/showthread.php?t=1620745](http://ubuntuforums.org/showthread.php?t=1620745)

where have i gone wrong here is what i have entered

SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin

00 3 * * *  /sbin/shutdown -h now

tks

You've been given suggestions in your previous thread.  You should test the suggestions given and update your other thread with the results.  This way the users who are trying to help you will see your update and comment on if you're doing it correctly or not.

Also, there might be others having a similar problem.  If you would contribute the responses and updates to that thread others might benefit from the progress.

The forum would sever as a better research resource by following his procedure also.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by rburkartjo on 2010-11-17
i made a link to an earlier thread that i had marked solved because toe gave me the answer i needed and if someone else wanted to do this  he provided the answer; however, i could not figure out how to do what he suggested.  so i did a work around; since my highest priority was to make sure my daughter computer shut down at a certain time during school day and another for the weekend just wrote a chron job that shuts the computer down at a certain time depending on the day and two other ones that each give a 5 min warning before the computer down at 10pm and  2pm.

---

### Post by rburkartjo on 2010-11-17
and i just put the jobs in here desktop so that they will run even if i wasnt still logged in

---

### Post by apollothethird on 2010-11-17
> **rburkartjo said:**
> i made a link to an earlier thread that i had marked solved because toe gave me the answer i needed and if someone else wanted to do this  he provided the answer; however, i could not figure out how to do what he suggested.  so i did a work around; since my highest priority was to make sure my daughter computer shut down at a certain time during school day and another for the weekend just wrote a chron job that shuts the computer down at a certain time depending on the day and two other ones that each give a 5 min warning before the computer down at 10pm and  2pm.
> **rburkartjo said:**
> and i just put the jobs in here desktop so that they will run even if i wasnt still logged in
Hi, Rburkarjo.  I believe your messages would be easier to read and have more efficiency if you would use a vertical space between thoughts rather than a full message between thoughts when posting.

Anyway, try putting a system wide cron job from root.  It’s unlikely that a normal user’s account will be able to shutdown another user’s session.

Try running:

sudo crontab -e

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by rburkartjo on 2010-11-17
tks apollo

---

