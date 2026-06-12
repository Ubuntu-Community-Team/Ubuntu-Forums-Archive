---
title: "whats the difference? 10.04 LTS and 10.10"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by REMIX8604 on 2011-01-27
i get they are different versions. one released in april and one in october. but does that fact that one is long term support make any difference? i love to keep updated on the latest versions of all my software, but being a newer linux user this LTS thing seems safer. am i stepping on to thin ice with 10.10? will 10.10 ever be LTS?

---

### Post by mharrison on 2011-01-27
There was a good discussion on this:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1094985](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1094985)

---

### Post by TeoBigusGeekus on 2011-01-27
> **REMIX8604 said:**
> am i stepping on to thin ice with 10.10?
Yes you are. LTS releases are generally more stable than usual ones. Unless you have a very specific reason to upgrade to 10.10 (kernel troubles for example), stay with lucid.

> **REMIX8604 said:**
> will 10.10 ever be LTS?
No. LTS releases are out every two years: before lucid(10.04-released on April of 2010), there was Hardy (8.04-released on April of 2008 ); the next one will be 12.04(will be released on April of 2012, if everything goes well - anyone remembers Dapper Drake?).

---

### Post by ikt on 2011-01-27
> **REMIX8604 said:**
> i get they are different versions. one released in april and one in october. but does that fact that one is long term support make any difference? i love to keep updated on the latest versions of all my software, but being a newer linux user this LTS thing seems safer. am i stepping on to thin ice with 10.10? will 10.10 ever be LTS?

LTS is generally intended for servers and places where upgrading every 6 months isn't optimal.

Go with 10.10 :)

---

### Post by marl30 on 2011-01-27
> **REMIX8604 said:**
> i get they are different versions. one released in april and one in october. but does that fact that one is long term support make any difference? i love to keep updated on the latest versions of all my software, but being a newer linux user this LTS thing seems safer. am i stepping on to thin ice with 10.10? will 10.10 ever be LTS?

At the moment, they are both stable. But for new users it's not a bad idea to start off with the LTS, especially the fact that it has been out for almost a year, so should be a lot more stable than 10.10.

---

### Post by REMIX8604 on 2011-01-27
i think i got it but let me make sure i have this correct. LTS is more of the main version that is released every 2 years. while the other releases are more like beta versions. the latest versions (non-LTS) will have all the newer features and supports more devices. and the LTS is stable and the updates are mainly for security and bug fixes.

how am i doing so far?

---

### Post by TeoBigusGeekus on 2011-01-27
> **REMIX8604 said:**
> i think i got it but let me make sure i have this correct. LTS is more of the main version that is released every 2 years. while the other releases are more like beta versions. the latest versions (non-LTS) will have all the newer features and supports more devices. and the LTS is stable and the updates are mainly for security and bug fixes.

how am i doing so far?

Although nobody in these forums will admit it, you've spoken a great truth.
You sir are a master and a scholar...

---

### Post by beew on 2011-01-27
> **REMIX8604 said:**
> i think i got it but let me make sure i have this correct. LTS is more of the main version that is released every 2 years. while the other releases are more like beta versions. the latest versions (non-LTS) will have all the newer features and supports more devices. and the LTS is stable and the updates are mainly for security and bug fixes.

how am i doing so far?

Actually not even bug fixes. The official repos have quite a bit of buggy and old softwares. The fear, I heard, is that fixing old bugs may lead to new bugs. You often get not only newer, but also less buggy versions from ppas. So unless you are planning to use a lot of ppas I would say either forget about the LTS or be prepared to be stuck with outdated and perhaps buggy software. 3 years is a long time in the developmental cycle of open source software. Remember if you are sticking to the official repo for the sake of "stability" you would be using software from a snapshot of Debian release before last April, between then and now many developments have taken place and if you stick to the official repo you will still be using the same two years from now.  "Stability" by the way means "doesn't change" and nothing else here, so it doesn't necessarily means something good.

10.10 so far works great on my systems. My plan would be to keep it til around Nov or early dec and then upgrade to 11.10. I will upgrade my 10.04 around the same time. I figure by then the ppas may dry up as more packagers will spend their time on newer versions and by then there may be too much incompatibility to backport newer software versions to Lucid . Basically my plan is to keep a LTS for a year and a half and a non LTS for a year.

Just my 2 cents, I am sure some will disagree. :)

---

### Post by cariboo on 2011-01-27
> **REMIX8604 said:**
> i think i got it but let me make sure i have this correct. LTS is more of the main version that is released every 2 years. while the other releases are more like beta versions. the latest versions (non-LTS) will have all the newer features and supports more devices. and the LTS is stable and the updates are mainly for security and bug fixes.

how am i doing so far?


An LTS version is only stable in that there won't be any major changes in the life-cycle of the release, otherwise, it's just as stable as most other releases, if your hardware is well supported, you shouldn't have any problems.

---

### Post by NightwishFan on 2011-01-27
Lucid and onward LTS releases have a much more conservative standard for importing packages. They base the release on Debian Testing instead of unstable, which in Debian packages have to have no release critical bugs to be in Testing. They also feature freeze much earlier and focus on bug fixes.

---

### Post by ssulaco on 2011-01-27
> **REMIX8604 said:**
> i get they are different versions. one released in april and one in october. but does that fact that one is long term support make any difference? i love to keep updated on the latest versions of all my software, but being a newer linux user this LTS thing seems safer. am i stepping on to thin ice with 10.10? will 10.10 ever be LTS?
Remix.....read this
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

Personally I recommend the LTS .......for stability.If you are in need of the latest and greatest,the LTS is probably not for you,unless like beew noted, you use alot of ppa's.
Download the release you are interested in..say 10.10...run it "live"....see how your hardware likes it.

---

### Post by QLee on 2011-01-28
> **NightwishFan said:**
> ...in Debian packages have to have no release critical bugs to be in Testing. ...

I just happened to notice this and there is a small correction, Debian "testing" (currently codename, squeeze) is where the release critical bugs are dealt with before the release  becomes the "stable" release. Until very close to release time there are always release critical bugs in the "testing" branch, more or less depending on how close to release. For example, today (UTC 12:00) there are 27 release critical bugs in squeeze.


REMIX8604,
I recommend the LTS for a new inexperienced user, you don't have to use it for the whole supported cycle but at first you might make fewer trips to the forum with questions while you are learning. One beauty of the Ubuntu live CD is that you can test newer versions on your hardware before you have to commit to an install. Another option that many like to do is multi-boot and keep a stable version for work and a newer version to test.

[Edit] As to your other question, no 10.10 will never become an LTS.

---

