---
title: "Best way to install software not in repository?"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-04-15
I've been reading that people generally don't recommend installing software that is not in the Ubuntu software repositories.  Is that generally true?

Is there a "safe," effective way to do it?

---

### Post by Chronon on 2011-04-15
It's all a matter of trust.  If you trust the project that produces the software AND you trust that they have taken sufficient measures to prevent tampering with binaries you might download then it's reasonable to install software from other sources.

You should take it on a case by case basis.

---

### Post by K_45 on 2011-04-15
Do you mean a PPA or a .deb file? I needed an external PPA for my Canon printer (don't ask) and some other repositories such as Medibuntu are safe, but it does depend.

---

### Post by Rubi1200 on 2011-04-15
In addition to the trust/security aspect, if you install something from outside the official repositories it will not be supported with updates from Canonical nor will you receive official support if it breaks something on your system; something else to consider.

---

### Post by Thewhistlingwind on 2011-04-15
What they really mean when they say that is that the software in the repos is usually quality checked and safe to install. Wheras when you install PPA's and .debs and compile from sources, you leave the much higher chance that theres malware hidden inside the software. In effect, everyone you install something from becomes a third party. Of course, chances are your already used to this environment, it's called the windows model. So, when installing from places that aren't the repos, act like a cautious windows user, and you should be good.

Also, theres the chance the software will break something, and the more obscure the software, the less the chance that we can help you with it.

---

### Post by wolfen69 on 2011-04-15
I've used PPA's with much success, but I can't speak for anyone else.

---

### Post by beew on 2011-04-15
"Official support" is meaningless if the package is broken and outdated. As an example I tried to install minitube in 11.04 beta yesterday and unbelievably the version in the official repo is still 1.3 (Natty is not even released yet) and it will be the version you install from the "officially supported" repo for the next 6 months. Hello?? 1.3 is not only old, it doesn't work for many people. I being one of them. When it came out I and other people wrote to the dev about our problems and he fixed them promptly in the next release. That was months ago and minitube 1.4x has been available for Lucid and Maverick through ppas also for months.

I install most of my end user softwares through ppas. Never had a problem that I couldn't get myself out of.
Think about it, the worst thing that a ppa can do is to mess up your system so bad that you have to install the whole system again, but this is highly unlikely. On the other hand, you are supposed to reinstall the whole system,--subject yourself to the worst case scenario when things go wrong,-- every 6 months to get updated softwares because.. it is more stable and secure??? Doesn't make any sense to me.

---

### Post by Paqman on 2011-04-15
> **beew said:**
> "Official support" is meaningless if the package is broken and outdated. As an example I tried to install minitube in 11.04 beta yesterday and unbelievably the version in the official repo is still 1.3

[Minitube is in Universe]("http://packages.ubuntu.com/maverick/minitube"), which is a community-maintained repo. Packages like this do depend on volunteers coming forward and packaging them. You need to bring this to the attention of the MOTUs to get it sorted.

---

### Post by beew on 2011-04-15
> **Paqman said:**
> [Minitube is in Universe]("http://packages.ubuntu.com/maverick/minitube"), which is a community-maintained repo. Packages like this do depend on volunteers coming forward and packaging them. You need to bring this to the attention of the MOTUs to get it sorted.

True but that does not negate my main point. Even if you alert them to include the latest release in the repo it still would stay the same for 7-8 months (the repos freeze months before final release) so that means if there are major updates or bug fixes you won't see them for 7-8 months and by that time they are likely not relevant any more. 7-8 months are  quite a long time for many fast moving projects, and that is, if you go through reinstalling the system every 6 months. Otherwise you software would be even more out of date (and probably broken)

---

### Post by K_45 on 2011-04-15
> **beew said:**
> True but that does not negate my main point. Even if you alert them to include the latest release in the repo it still would stay the same for 7-8 months (the repos freeze months before final release) so that means if there are major updates or bug fixes you won't see them for 7-8 months and by that time they are likely not relevant any more. 7-8 months are  quite a long time for many fast moving projects, and that is, if you go through reinstalling the system every 6 months. Otherwise you software would be even more out of date (and probably broken)

What about backports for bug fixes?

---

### Post by beew on 2011-04-15
> **K_45 said:**
> What about backports for bug fixes?

How many programs do you find in the backports? Backport is a good idea but only on paper, in fact it is not much use. I don't see too many bug fixes either except for something security related.

---

### Post by Paqman on 2011-04-15
> **beew said:**
> 7-8 months are  quite a long time for many fast moving projects

Which is exactly exactly what PPAs are for.

---

### Post by beew on 2011-04-15
> **Paqman said:**
> Which is exactly exactly what PPAs are for.

This is what I am arguing for. :) Someone here seem to be arguing against them because they are not 'officiially supported".

---

