---
title: "quick cron question"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by pqwoerituytrueiwoq on 2011-06-17
if i set a cron job up under my user will that job be run if i am not logged in?
or would root need to run the cron job for it to work at the login screen

---

### Post by jtarin on 2011-06-17
> **pqwoerituytrueiwoq said:**
> if i set a cron job up under my user will that job be run if i am not logged in?
or would root need to run the cron job for it to work at the login screenThe quick answer is....No....not for user unless your logged in. However, you can run a job as root before login. Here's a link to some documentation that will clarify more than I could in this post. It gives you examples to run and ways to find out if it was successful. I think Anacron is what you looking for...it's mentioned in the documentation.

---

### Post by pqwoerituytrueiwoq on 2011-06-17
thanks

---

### Post by jtarin on 2011-06-17
Glad I could be of some help.

---

### Post by DaithiF on 2011-06-18
> **pqwoerituytrueiwoq said:**
> if i set a cron job up under my user will that job be run if i am not logged in?


Yes, cron runs jobs for users regardless of whether or not they are logged in.  Thats one of the key features of cron actually ... the ability to run jobs unattended.  As long as the PC is on, and the cron daemon running your jobs will get run.

---

### Post by jtarin on 2011-06-18
> **DaithiF said:**
> Yes, cron runs jobs for users regardless of whether or not they are logged in.  Thats one of the key features of cron actually ... the ability to run jobs unattended.  As long as the PC is on, and the cron daemon running your jobs will get run.
And your right too, but certain parameters must be setup allowing for the environment......it's a question with two not so brief and clear-cut answers. I suggest the OP read the Cron manpages and Google crontab.

---

