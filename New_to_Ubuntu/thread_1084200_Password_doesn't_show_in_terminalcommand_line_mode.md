---
title: "Password doesn't show in terminal/command line mode when typing?"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-01
Hey,
whenever I use the sudo command and it asks for my password, I type the password and hit enter, and it works, but whilst I'm typing the password I can't actually see it?

There's no cursor or anything to indicate characters being typed....


Just wondering if this is normal? how to fix?
etc...


Thanks!

---

### Post by snova on 2009-03-01
It is meant to be that way, as a security feature.

---

### Post by SunnyRabbiera on 2009-03-01
correct, there is no indication of your password in the terminal for a good reason.

---

### Post by whoop on 2009-03-01
First time I have seen a question like this. It is not a stupid question Imo. Everywhere else you type a password you are presented with asterisks or dots or something. I even remember this application that displayed weird characters to distract users that could be looking over your shoulder.
I can understand that no feedback (in any way) may give users the idea that no input is received.

---

### Post by Gp. on 2009-03-01
Is there a way to have it show the black dots at least?

---

### Post by SunnyRabbiera on 2009-03-01
I dont think so, at least not to my knowledge.

---

### Post by whoop on 2009-03-01
> **Gp. said:**
> Is there a way to have it show the black dots at least?
I haven't seen that. Don't think it's available.

---

### Post by snova on 2009-03-01
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/194472](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/194472)

No. However, look at the last post:

> Upstream now added a "pwstars" option in cvs head, which will be released as 1.7.0.

This is from last month, so there's a chance you'll see it in Jaunty. Until then, no.

---

### Post by Temposs on 2009-03-01
I teach an intro computer science course for non-majors at my university, and the students do get totally confused by this feature of the Linux terminal. They assume that it's not working, and call me over and show me by tapping a few keys and get a flustered look on their face. Once it's explained it's fine, but it's not entirely intuitive for most users, since there is feedback in basically every other password interface they use, even in GNU/Linux apps.

---

### Post by louieb on 2009-03-01
Not displaying * or . or something else - is the *nix way of password entry. 

:confused:Saw a bug report in Launchpad once. It was closed, so don't expected it to change anytime soon.

---

### Post by Gp. on 2009-03-01
> **snova said:**
> [https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/194472](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/194472)

No. However, look at the last post:



This is from last month, so there's a chance you'll see it in Jaunty. Until then, no.


"Upstream now added a "pwstars" option in cvs head, which will be released as 1.7.0. "

Hi,
What is a cvs head? and how will this be enabled in Jaunty?

Thnx.

---

### Post by snova on 2009-03-01
> **Gp. said:**
> What is a cvs head?

The code that sudo developers are working on, the very latest. Of course, this was a month ago, so it's no longer HEAD, but the point is that they added it.

> and how will this be enabled in Jaunty?

It isn't necessarily. sudo would make another release, and Ubuntu developers would have to decide to update to it. It might also be too late to get into the next release.

And even then, it's only an option- there's no telling whether it'd be enabled by default. (I suspect not.)

---

### Post by Walter Melon on 2009-03-02
> **whoop said:**
> First time I have seen a question like this. It is not a stupid question Imo. Everywhere else you type a password you are presented with asterisks or dots or something. I even remember this application that displayed weird characters to distract users that could be looking over your shoulder.
I can understand that no feedback (in any way) may give users the idea that no input is received.

What application is that?  It sounds like it would be very cool, or at the very least, fun to watch.

---

