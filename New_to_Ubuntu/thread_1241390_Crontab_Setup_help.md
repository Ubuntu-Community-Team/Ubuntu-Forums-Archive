---
title: "Crontab Setup help"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by aufan19 on 2009-08-15
Hi everyone,

I think I am going to start using Cron for a couple of things, and I had a few questions about it. If I wanted to have something run at 7:00 only on Mondays from August until May is this how it would be set up?

0 19 * 8-5 1

or would I have to do this:

0 19 * 8,9,10,11,12,1,2,3,4,5 1

I read that crontab sends an e-mail to the user's account when it runs. I know this can be disabled, but where does the e-mail get sent to if you don't specify a "MAILTO="? Or does that not happen if you don't specify one?

Thanks

---

### Post by squaregoldfish on 2009-08-16
I don't know for certain whether you can set a range to wrap around zero, so it might be safer to specify the months individually. Or you could set two ranges:

0 19 * 1-5,8-12 1

Of course, you can always run some experiments with the minutes value to find out.

As for the email, if you set

MAILTO=""

no email is sent.

Steve.

---

