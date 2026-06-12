---
title: "seperate /home partition?"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by gabriella on 2009-04-28
How exactly do I move my /home directory to I separate partition?. I mean I know how to create a new partition no problem but I seem to remember reading about some procedure to shift the /home over. I recall seeing a tutorial somewhere on the subject?

Thanks

---

### Post by Praxicoide on 2009-04-28
Here you go:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by anjilslaire on 2009-04-28
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by wizard10000 on 2009-04-28
> **gabriella said:**
> How exactly do I move my /home directory to I separate partition?. I mean I know how to create a new partition no problem but I seem to remember reading about some procedure to shift the /home over. I recall seeing a tutorial somewhere on the subject?

Thanks

The easiest way to do it is to back up your home directory to another location, create the new partition, edit /etc/fstab to reflect the location of the new home directory and then restore the data.

Here's a pretty good tutorial -

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by wizard10000 on 2009-04-28
Apparently great minds think alike  ;)

---

### Post by gabriella on 2009-04-28
Thanks everyone! Thats what I was looking for!

---

### Post by gabriella on 2009-04-28
Oh BTW Praxicoide, Love your avatar!!

---

### Post by Praxicoide on 2009-04-28
I think I took it from some MS blogger's anti-linux rant. :)

---

### Post by abhiroopb on 2009-04-28
I personally would not suggest using psychocats guide. I did it and it caused problems later on. For example, running certain commands wouldn't work. Without going into too much detail I would suggest backing up your data, deleting everything and re-partitioning witha  separate /home partition.

---

### Post by egalvan on 2009-04-28
> **abhiroopb said:**
> I personally would not suggest using **psychocats guide**.
 I did it and it **caused problems later on**.
 For example, **running certain commands wouldn't work**.
 Without going into too much detail I would suggest **backing up your data,** deleting everything and re-partitioning witha  separate /home partition.

psychocat's guides have been used for a long time...
I have personally used several...

No issues.

Can you proved us with **SPECIFIC** information regarding the errors and problems you claim to have encountered?

psychocat is also an outstanding member of this forum...
his advice and help here have been excellent...

Again, no problems.

Althougn almost all long-time users would agree to **BACK UP YOUR DATA** before messing with partitions.

ErnestG

---

### Post by Irony on 2009-04-28
You would use the second part of the method I outline here;

[http://ubuntuforums.org/showthread.php?t=416710](http://ubuntuforums.org/showthread.php?t=416710)

Plus see the link at the end of the guide. It works 'cos I've done it many times.

---

### Post by abhiroopb on 2009-04-28
Wow, easy there. I never said I thought psychocats' guides in general were bad or anything like that.

As you well know ubuntu is very tempremental, while it works well enough for me NOW, many users have reported problems. Just because it worked for you doesn't mean that it works fine for everyone else.

If you want to know specifics...
This was a cosmetic problem I remember. whenever I would use gnome-do to launch "home" it would return an error saying the location could not be found.

---

### Post by SentientFluid on 2009-04-28
> **egalvan said:**
> Can you proved us with **SPECIFIC** information regarding the errors and problems you claim to have encountered?

While it's nice to see people defend other members od the community, Psychocat has posted disclaimers at the beginning of that article stating it may not work for everyone...

> I and others have been successful in creating a separate /home partition using this tutorial, *but *there are many who have had difficulty being successful with the process. If you are not confident in what you're doing or in repairing or recovering from this process should anything go wrong, then *do not attempt the instructions outlined here*. I cannot help you troubleshoot problems that result from following this tutorial.

Emphasis is Psychocats.

So lesson to us all... ALWAYS read the disclaimers.  They're there to protect you. :)

---

### Post by abhiroopb on 2009-04-28
> **SentientFluid said:**
> While it's nice to see people defend other members od the community, Psychocat has posted disclaimers at the beginning of that article stating it may not work for everyone...



Emphasis is Psychocats.

So lesson to us all... ALWAYS read the disclaimers.  They're their to protect you. :)

Thanks for pointing that out :)

---

### Post by egalvan on 2009-04-28
If I came off as harsh, well, it's the major problem with the printed word, versus speech...
 If I had spoken my post, you would have noticed no harshness,
only a plea for more information...

maybe I should have put in a couple of :) ?

or even :lolflag:


So...
Yep, I **ABSOLUTELY** agree that **ANY** tutorial or hint or help can mess up a system, or fail to work...

Which is why when conscientious writers such as psychocat post help,
they also post the warnings about what such help can help or mess up.

And I agree that **they should be heeded**.


To continue...

If you had stated:

"I followed this guide, and it did not work exactly right for me.
This is what failed... (insert failure here)
If you want to try it yourself, be sure to **HEED THE WARNINGS** about backing up your precious data"

But when someone states:
"I personally would not suggest using psychocats guide.
 I did it and it caused problems later on.
 For example, running certain commands wouldn't work",

well,
it's rather vague.


I'm sorry, but vague "it didn't work" posts are not particularly helpful.
It's (nearly) impossible to re-create the problem, and thus near-impossible to try to fix it.

And I know for a fact that psychocat is responsive to reports of errors in his guides, as well as his forum posts.

Give him a chance to fix problems, or to suggest work-arounds...

I have no connection to psychocat, have never met him/her,
I'm sure he is fully capable of defending himself (or not),
but I do care about helping the community at large.

The more information, the better for everyone...
poster, reader, helper, helpee...

---

### Post by SuperSonic4 on 2009-04-28
Eh, if you're doing *anything* with partitioning then essential data should be backed up externally

---

### Post by abhiroopb on 2009-04-28
> **egalvan said:**
> If I came off as harsh, well, it's the major problem with the printed word, versus speech...
 If I had spoken my post, you would have noticed no harshness,
only a plea for more information...

maybe I should have put in a couple of :) ?

or even :lolflag:


So...
Yep, I **ABSOLUTELY** agree that **ANY** tutorial or hint or help can mess up a system, or fail to work...

Which is why when conscientious writers such as psychocat post help,
they also post the warnings about what such help can help or mess up.

And I agree that **they should be heeded**.


To continue...

If you had stated:

"I followed this guide, and it did not work exactly right for me.
This is what failed... (insert failure here)
If you want to try it yourself, be sure to **HEED THE WARNINGS** about backing up your precious data"

But when someone states:
"I personally would not suggest using psychocats guide.
 I did it and it caused problems later on.
 For example, running certain commands wouldn't work",

well,
it's rather vague.


I'm sorry, but vague "it didn't work" posts are not particularly helpful.
It's (nearly) impossible to re-create the problem, and thus near-impossible to try to fix it.

And I know for a fact that psychocat is responsive to reports of errors in his guides, as well as his forum posts.

Give him a chance to fix problems, or to suggest work-arounds...

I have no connection to psychocat, have never met him/her,
I'm sure he is fully capable of defending himself (or not),
but I do care about helping the community at large.

The more information, the better for everyone...
poster, reader, helper, helpee...

I'd just like to clarify a few things. Without (hopefully) being overly pedantic, 

as you mentioned I gave MY opinion on the subject. Stating that it had NOT worked for me. How much clearer does that need to be? I apologise for not following your script, but I feel I gave adequate reasoning for not using a certain solution. I gave what failed. Perhaps I did not specifiy the exact command, but that is my prerogative. And I did clarify later. The point is the OP is not obliged to follow my advice, but I have every right to give that advice without being reprimanded for doing so. I did not say psychocat's guides were bad, or even that this one was bad. I simply said that it caused me problems. At the end of the day disclaimers are useful, however, they are useful only to a certain extent since virtually all guides on the internet come with disclaimers its difficult to filter out ones that are genuinely problematic v the ones that might work. Therefore, my comment was merely highlighting a possible failing of that particular guide without going into detail. I even offered an alternative solution.

Again I apologise for not going into detail in the first case, however, the comment was directed at the OP and not psychocats.

---

