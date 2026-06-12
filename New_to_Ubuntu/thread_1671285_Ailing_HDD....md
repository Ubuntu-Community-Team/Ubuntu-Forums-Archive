---
title: "Ailing HDD..."
date: 2011-01-19
forum: New to Ubuntu
---

### Post by dmcdow on 2011-01-19
Dear All,

I searched for a specific answer to this question, honest, but did not find anything that is a sort of a "how to".  Please bear with me.
I have been using Ubuntu 10.10 since October 2010 and have gotten it tweaked just right (I think).  Then I found smartmontools.  Apparently, I have an ailing HDD (please see smartmontools output below (I think I attached it right)).  
From what I can tell this HDD is on its way out.  When I see "old age" and "Pre-fail", that makes me believe it ain't going to be long.  Please correct me if you think not.
I will replace this ailing HDD in early February.  I would like to put my current customized Ubuntu on the new HDD and jettison the old HDD.  This would mean that the new one would have to be partitioned then made bootable then copied, I guess.  I am familiar with using Disk Utility to partition/format the drive.  I get lost after that.
My questions are: 
How do I make the new HDD Ubuntu bootable?
How do I copy (clone?) an exact copy of what is on the old HDD to the new HDD so that I don't have to re-download everything that I have currently installed on the old HDD?
BTW, I've attached the output of lshw too.

Thank you for any information (and your patience),
David

---

### Post by audiomick on 2011-01-19
Hallo.
firstly, a better way to post that sort of output is to use the "code" tage. That is the # symbol at the top of the post window. Click on it, and paste your content between the code and /code in square brackets.

secondly, is it believable that your drive is aging? How old is it?

---

### Post by dmcdow on 2011-01-19
Dear audiomick,

Thank you for your reply and the information on how to post code... I will use your advice in future posts.

The computer is approximately 7 years old, so I suspect that it is reasonable to think that the HDD is on its to dying.

Thank you again for your previous reply and a future reply,
David

---

### Post by srs5694 on 2011-01-19
You're mis-reading the report. The single most important item is this:

```
SMART overall-health self-assessment test result: PASSED 

```

In other words, the drive is fine. The "old age" and "pre-fail" strings you mention refer to the *type* of test each item is -- so for instance, "start-stop count" is an "old age" test, meaning that *if or when* it exceeds a threshold, the disk is considered old and at higher risk of failure; and "reallocated sector count" is a "pre-fail" test, meaning that when that value begins to go up beyond its threshold, it's a sign that failure is imminent.

These terms are alarming, and I wish they'd expressed them more clearly. I, too, was getting very concerned the first time I looked at a SMART output. Then I realized that *all* of my drives had the same alarming terms in them!

---

### Post by audiomick on 2011-01-19
> **srs5694 said:**
> You're mis-reading the report. The single most important item is this:

```
SMART overall-health self-assessment test result: PASSED 

```In other words, the drive is fine. The "old age" and "pre-fail" strings you mention refer to the *type* of test each item is --
That's why I asked about the age. I have fallen for that myself, and have to read the output of smartmontools several times to make sense of it.

7 years is old enough to be suspicious, but if the drive has passed, it is alright for now. No reason not to do backups, though... ;)

---

### Post by dmcdow on 2011-01-19
Dear srs5694 and audiomick,

Thank you so much for your reply.  You just saved me a huge headache and some money... I'll buy a nice beer and toast in your honor.  I knew there had to be more to my interpretation.

Not to pontificate or get all sappy, but I am highly encouraged by becoming a Ubuntu/Linux user (again) and by the community support.  
I am a user.  My computer use started in about 1989 when my boss bought a PC (with the 5 1/2" floppy drives) and said "... figure out how to use this thing".  Being a land surveyor, I turned it on and saw a blinking cursor and though what the f..., but finally figured how to use it (aah Norton Editor).

I tried Red Hat in about 1992 or '93 and was discouraged because I'm a land surveyor dammit.  I gave up.

My computer is now old, I am broke, and figured I'd look into Linux again.  I'm glad I did.  It has revived my computer and I am able to be productive without spending money on a perfectly great system.  

Thank you (all) again for you input/advice,
David

---

### Post by dmcdow on 2011-01-19
Thanks again,
David

---

