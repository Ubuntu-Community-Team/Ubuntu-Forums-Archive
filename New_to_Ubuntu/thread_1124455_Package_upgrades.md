---
title: "Package upgrades"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by MisterP on 2009-04-13
Here's a thought:  why does Ubuntu have packages that are outdated.  For instance; open office on ubuntu is at version 2.4, but I am aware of a version 3.0.  Similarly, the version of clamav seems to be outdated.
Now, I know Ubuntu 9.4 is due out and maybe that upgrade will address some of the package outdated issues.
But, doesn't Ubuntu upgrade packages mid system release?
I have looked about on the internet, but got no satisfactory answers.  My own thoughts are that perhaps Ubuntu doesn't jump to upgrade packages immediately because there is no need.  Rather it sticks with reliable, stable packages until the new ones prove themselves?
Maybe.
What does anyone else think?

---

### Post by leonardo_neo on 2009-04-13
You are right, stability is the first priority.

But it is not 100% true that they don't 'upgrade' the applications. You are right about Open Office, but examples like that are very few. 

The 9.04 has newer version of Open office. 

Moreover, you can manually upgrade things on your own.

---

### Post by Hospadar on 2009-04-13
The reason is because package maintainers don't like to do major version upgrades (Ooo 2.4 - 3.0 for example) in anything but a new distrobution (ibex to jaunty for example)

The thinking is that if you had systems in production (At a business, on a server) you wouldn't want updates getting automatically added that might break your system.

As a regular desktop user though, you probably don't care, because you have the time to monkey with your installation if some upgrade doesn't go perfectly to plan (as opposed to IT people who can't monkey with a hundred installations)

If you want, you can add the "backports" repository in System->Administration->Software Sources.  This repo has these sorts of upgrades that get ported back from newer (including beta) versions of ubuntu.  Often times the major version upgrades will go here and not in the main repos.

---

### Post by MisterP on 2009-04-13
Thanks for the info.
I'm still a bit scared about manually doing things, but I'll just have to learn!

---

### Post by moredhel on 2009-04-13
Or in the case of OO.o 3.0, you could wait 10 days ;)

---

### Post by Paqman on 2009-04-13
> **MisterP said:**
> Thanks for the info.
I'm still a bit scared about manually doing things, but I'll just have to learn!

It's a doddle. In the case of Open Office, just go to their site and download the .deb package. Then just click on it to install. Couldn't be simpler.

---

### Post by moredhel on 2009-04-13
Sounds like installing stuff in windows ;)

---

