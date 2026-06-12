---
title: "Add/Remove Applications list is empty"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by locustfist on 2009-01-27
Running Ibex

Doesn't matter what option I select from the 'Show:' drop down. I cannot get any apps to show.

Any ideas?

---

### Post by ssdurn on 2009-01-27
I have exactly the same issue...

---

### Post by SunnyRabbiera on 2009-01-27
Well to make sure everything is fine see what happens when you use synaptic, located under system> administration> synaptic package manager.
Synaptic does the same job as add/remove

---

### Post by locustfist on 2009-01-27
> **SunnyRabbiera said:**
> Well to make sure everything is fine see what happens when you use synaptic, located under system> administration> synaptic package manager.
Synaptic does the same job as add/remove

That works.

I installed an app from there successfully (filezilla).

then i checked the add/remove to see if it changes...it didn't

---

### Post by SunnyRabbiera on 2009-01-27
You may need to refresh apt, did you hit the reload button in synaptic?
It might do the job but worse comes to worst I might have you open a terminal...
But lets do that last to see if things are okay.

---

### Post by locustfist on 2009-01-27
> **SunnyRabbiera said:**
> You may need to refresh apt, did you hit the reload button in synaptic?
It might do the job but worse comes to worst I might have you open a terminal...
But lets do that last to see if things are okay.

Didn't work.

---

### Post by SunnyRabbiera on 2009-01-27
Alright, well first things first.
Make sure that synaptics closed
make sure add/remove is closed
open a terminal by going to applications> accessories >terminal
After it opens copy and paste this command:
sudo apt-get update

it will ask for a password, use your password and see if it will fix any errors.
If add/remove still doesn't work, just forget about it and use synaptic as it does the same basic job.

---

### Post by locustfist on 2009-01-27
> **SunnyRabbiera said:**
> Alright, well first things first.
Make sure that synaptics closed
make sure add/remove is closed
open a terminal by going to applications> accessories >terminal
After it opens copy and paste this command:
sudo apt-get update

it will ask for a password, use your password and see if it will fix any errors.
If add/remove still doesn't work, just forget about it and use synaptic as it does the same basic job.

Bummer, didn't work.

Thanks for the help. I should be good to go with the synaptic manager.

---

### Post by SunnyRabbiera on 2009-01-27
> **locustfist said:**
> Bummer, didn't work.

Thanks for the help. I should be good to go with the synaptic manager.

Yeh synaptic is easy enough to understand for anyone I feel, actually it was because of synaptic that I use ubuntu and debian based systems.

---

