---
title: "pop email not being retrieved any more?"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by kapi on 2009-07-22
have used evolution for seven months now with no problems but a few days ago I noticed no email was being downloaded from gmail, does anyone have any ideas?

I have reset the pop download setting in gmail, checked all the settings in the mail client to no avail.

has anyone else had this problem?

---

### Post by mhurst102282 on 2009-07-22
Mine does work so here are a few questions. What version are you using? Also have you tried opening it in a terminal to see if any errors pop up?

---

### Post by wojox on 2009-07-22
Evolution has a 2 gig mailbox size limit bug. That is what you might be seeing.

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/197290](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/197290)

---

### Post by kapi on 2009-07-22
Actually I think it may be gmail thats the problem because I tested downloading in thunderbird too and I'm having major problems


thanks though

---

### Post by Wataru8675 on 2009-07-22
> **kapi said:**
> Actually I think it may be gmail thats the problem because I tested downloading in thunderbird too and I'm having major problems


thanks though
 
It must be gmail.  I'm having the exact same problem with my gmail account on Evolution.

---

### Post by mhurst102282 on 2009-07-22
It works for me

---

### Post by Wataru8675 on 2009-07-22
> **mhurst102282 said:**
> It works for me

That's odd...you're talking about a gmail account, right?

---

### Post by mhurst102282 on 2009-07-22
Yes I am it is working perfectly, but I do also have the occsional hiccup so maybe gmail is just doing some work on your account.

---

### Post by mudcat on 2009-07-22
it must be gmail; sometimes my thunderbird has trouble connecting to the gmail server and has lasted as long as a day or so

---

### Post by Codix121 on 2009-07-22
Uhm this might not very useful but in my opinion switch to Thunderbird,
it's by mozilla and in my personal opinion works much better :)
It also has cool customizable settings and it just works very well for me,
Evolution kept giving me trouble :(

---

### Post by Wataru8675 on 2009-07-23
> **Codix121 said:**
> Uhm this might not very useful but in my opinion switch to Thunderbird,
it's by mozilla and in my personal opinion works much better :)
It also has cool customizable settings and it just works very well for me,
Evolution kept giving me trouble :(

Oh, jeez, I installed Thunderbird and my problem was immediately solved.  Thanks!

---

### Post by LewRockwell on 2009-07-23
Mozilla Firefox and Thunderbird are both outstanding!

If it's any consolation, other have experienced problems with gmail

then, of course, there was that time they were completely down for a couple of hours

.

---

### Post by SaaTeeVaaGreen on 2009-07-23
i have been having exactly the same problem with my gmail account *and* my yahoo account for maybe a week now. think i will be giving thunderbird a try as well...

---

### Post by wizard10000 on 2009-07-23
> **LewRockwell said:**
> Mozilla Firefox and Thunderbird are both outstanding!

OT, but I pitched Evolution for claws-mail and have been happy.  I can't abide Thunderbird.  claws-mail is light, fast and doesn't have all the bloatware.

I will say that most of the plugins in the Ubuntu repos for claws-mail don't work because they're the wrong version so I get claws-mail from Launchpad repos.

edit:  I also use gmail - and have an iCal plugin for claws-mail so I can access my Google calendar.

---

### Post by andrew.46 on 2009-07-24
Hi kapi,

> **kapi said:**
> have used evolution for seven months now with no problems but a few days ago I noticed no email was being downloaded from gmail, does anyone have any ideas?

I had same problem at the same time. Have a look at:

[http://www.google.com/accounts/DisplayUnlockCaptcha](http://www.google.com/accounts/DisplayUnlockCaptcha)

which may very well solve the problem.

Andrew

---

