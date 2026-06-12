---
title: "what does &quot;upstream&quot; mean?"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by Chris1274 on 2010-09-02
I was just listening to Mark Shuttleworth's Google talk and he referred a bunch of times to "upstream," which is something I've seen mentioned elsewhere too. Can anyone enlighten me as to what it means? Thanks.

---

### Post by amauk on 2010-09-02
Upstream refers to component software projects that feed into a larger collection

- Debian is upstream of Ubuntu
The Debian distro feeds into Ubuntu

- Fedora is upstream from RHEL

- The Linux kernel, GNU utilities, X.org, all the desktop environments, etc. etc. are upstream from Linux distros

---

### Post by Bachstelze on 2010-09-02
> **amauk said:**
> 

- Debian is upstream of Ubuntu
The Debian distro feeds into Ubuntu



While technically true, you won't hear anyone in Ubuntu refer to Debian as "upstream". Debian is refered to as Debian, and "upstream" in Ubuntu means the same thing as it does in Debian: the developers of the pieces of software that get packaged.

---

### Post by Thryn on 2010-09-02
> **Bachstelze said:**
> While technically true, you won't hear anyone in Ubuntu refer to Debian as "upstream". Debian is refered to as Debian, and "upstream" in Ubuntu means the same thing as it does in Debian: the developers of the pieces of software that get packaged.

I seem to recall seeing that exact phrase on an Ubuntu wiki somewhere. Something about a bug report being sent "upstream to Debian" because the relevant program was part of Debian, not Ubuntu-specific. And I wasn't able to find that exact page but if you search for "upstream to Debian" there are Ubuntu-related results [(such as this one)]("https://wiki.ubuntu.com/Debian/PythonModulesTeam"). So maybe it isn't common, but it happens. Admittedly some of the results were written by Debian folks.

---

### Post by valbaca on 2010-09-02
The analogy is a river.

Individual projects (X.org, GNOME, Firefox, etc.) are "upstream" and their programs flow down the river to Ubuntu (or any other distro). Like water, this flow isn't instantaneous because these programs have to be tested and packaged before they can be put in the Ubuntu sources for apt-get. 

(I'm not trying to hijack this thread, only trying to provide a context with as little personal commentary as possible)
The current hot topic with "upstream" is whether Ubuntu (sitting at the bottom of the river and collecting everything that flows from the free software community) is in fact contributing back (back to the upstream) or if it just keeps to itself. I use "Ubuntu" to obviously mean the Ubuntu community and developers.
There is also the relationship between Ubuntu and it's most influential and not-totally-compatible upstream: Debian. 
I hope I didn't just kick a hornet's nest :)

---

### Post by srs5694 on 2010-09-03
As the developer of [GPT fdisk (gdisk),](http://www.rodsbooks.com/gdisk/) which is now included in Ubuntu, I'll add this: My own project has benefitted, albeit in fairly small ways, from downstream contributions -- that is, from distribution developers. For instance, the Fedora developers contributed an improved RPM .spec file (which is used to build RPMs, the equivalent of Debian packages), and I've gotten suggestions for file naming and other improvements from Debian developers. To date, most or all of the actual code patches I've received have come from individuals unrelated to distributions, although it's possible I'm forgetting something.

Downstream developers and users can certainly contribute to upstream projects. Even if it's just bug reports, I'd certainly appreciate hearing from downstream projects rather than let problems go unfixed or limitations unaddressed. Note that I'm not complaining about Ubuntu's contribution or lack thereof to GPT fdisk; I'm just commenting that *if* a user or distribution maintainer finds a bug or perceives the desirability of a new feature, it's in their own best interest to report it to the upstream developer. In the absence of such reports, problems might never be fixed. Of course, upstream developers vary in personality, available time, and so on, so bug reports and suggestions might or might not be addressed in a timely way; but I think most open source developers will at least make an effort to address real problems.

---

### Post by valbaca on 2010-09-03
> **srs5694 said:**
> As the developer of [GPT fdisk (gdisk),]("http://www.rodsbooks.com/gdisk/") which is now included in Ubuntu, I'll add this: My own project has benefitted, albeit in fairly small ways, from downstream contributions -- that is, from distribution developers. For instance, the Fedora developers contributed an improved RPM .spec file (which is used to build RPMs, the equivalent of Debian packages), and I've gotten suggestions for file naming and other improvements from Debian developers. To date, most or all of the actual code patches I've received have come from individuals unrelated to distributions, although it's possible I'm forgetting something.

Downstream developers and users can certainly contribute to upstream projects. Even if it's just bug reports, I'd certainly appreciate hearing from downstream projects rather than let problems go unfixed or limitations unaddressed. Note that I'm not complaining about Ubuntu's contribution or lack thereof to GPT fdisk; I'm just commenting that *if* a user or distribution maintainer finds a bug or perceives the desirability of a new feature, it's in their own best interest to report it to the upstream developer. In the absence of such reports, problems might never be fixed. Of course, upstream developers vary in personality, available time, and so on, so bug reports and suggestions might or might not be addressed in a timely way; but I think most open source developers will at least make an effort to address real problems.
Well put :D Good to hear from a dev

---

