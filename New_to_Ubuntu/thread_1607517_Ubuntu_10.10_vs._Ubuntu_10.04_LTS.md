---
title: "Ubuntu 10.10 vs. Ubuntu 10.04 LTS"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by albertwt on 2010-10-27
Hi All,

I'm relatively new to this environment, is there any differences between Ubuntu 10.10 vs. Ubuntu 10.04 LTS ?

I'm planning to deploy Linux VM in datacenter but is there any beneftis installing the non LTS version ?

Thanks

---

### Post by uRock on 2010-10-27
Newer kernel that has better support for newer hardware, but other than that it isn't much different from 10.04. If you are going to use is as a data server. then you may want to use the LTS for better longevity.

---

### Post by GabrielYYZ on 2010-10-27
10.04 worked beautifully for me the short time i had it (discovered it a week before 10.10 came out) but 10.10 isn't bad at all. i switched to 10.10 the day after it came out and i don't see any difference, other than the network manager working better for me on 10.10. 

as for benefits, i don't really see any but, then again, i'm completely clueless about Linux VM in datacenter. so, there may be benefits regarding that particular situation, i just don't know 'em.

---

### Post by ericdn on 2010-10-27
I agree that the differences between 10.10 and 10.04 aren't major, but those that exist are, in my opinion, rather positive.  I *love* the new Applications Center in 10.10 - its format and setup are the best I've ever seen on Ubuntu.  And, at least in the Russian version of 10.10 that I use, the standard system fonts are also improved.

---

### Post by albertwt on 2010-10-27
Ah..

Thanks guys for your reply, however "Applications Center in 10.10" --> this doesn't apply to me since I'm installing server edition which is controlled using SSH console.

one thing that I found out is that i got stuck in installing VMware tools in Ubuntu 10.10 server but not in 10.0.04.1 LTS.

---

### Post by e79 on 2010-10-27
> **uRock said:**
> Newer kernel that has better support for newer hardware, but other than that it isn't much different from 10.04. If you are going to use is as a data server. then you may want to use the LTS for better longevity.

+1
Aiming at a Data servers in Data centers and maybe major deployment (I don't know if you plan for the latter) I would personally stick with the LTS edition rather than the 6 months normal releases.

---

### Post by ofb on 2010-10-28
You probably want the LTS version.

Basics:

Ubuntu has a 6 month release cycle. Every third release is an LTS.

Normal releases are supported with updates from Canonical for 18 months. LTS versions are supported with updates for 3 years.

LTS server versions are supported with updates for 5 years.

What support mostly means is you get security & bug updates.

But you don't get major version updates of applications until you go to the next version of Ubuntu. This part confuses people a little sometimes. Let me try an example.


Say you've got fictional app Foo 2.0 on Lucid.

Typically version numbers like 2.1, 2.2, 2.3 etc, will be security & bug fixes for 2.0 released by the developers of Foo.

Canonical will test these new sub-versions, and pass them on to you in Lucid.

The version number 3.0 will usually be reserved for major feature changes. When 3.0 comes out, Canonical will schedule that for a future release of Ubuntu. They will not pass it to you in Lucid.

However, typically Foo 3.0 also contains some security fixes. When that occurs, Canonical will make a special 2.x_ubuntu version with just those fixes to pass on to you in Lucid, so that your Foo 2.x isn't in danger.


So basically, if you like to have the latest versions of apps with the latest features, you want to follow the 6 month release cycle.

If you're less interested in staying abreast of the latest features, and more interested with extending the time between Ubuntu upgrades, go with the LTS releases.

---

### Post by albertwt on 2010-10-28
> **ofb said:**
> You probably want the LTS version.

Basics:

Ubuntu has a 6 month release cycle. Every third release is an LTS.

Normal releases are supported with updates from Canonical for 18 months. LTS versions are supported with updates for 3 years.

LTS server versions are supported with updates for 5 years.

What support mostly means is you get security & bug updates.

But you don't get major version updates of applications until you go to the next version of Ubuntu. This part confuses people a little sometimes. Let me try an example.


Say you've got fictional app Foo 2.0 on Lucid.

Typically version numbers like 2.1, 2.2, 2.3 etc, will be security & bug fixes for 2.0 released by the developers of Foo.

Canonical will test these new sub-versions, and pass them on to you in Lucid.

The version number 3.0 will usually be reserved for major feature changes. When 3.0 comes out, Canonical will schedule that for a future release of Ubuntu. They will not pass it to you in Lucid.

However, typically Foo 3.0 also contains some security fixes. When that occurs, Canonical will make a special 2.x_ubuntu version with just those fixes to pass on to you in Lucid, so that your Foo 2.x isn't in danger.


So basically, if you like to have the latest versions of apps with the latest features, you want to follow the 6 month release cycle.

If you're less interested in staying abreast of the latest features, and more interested with extending the time between Ubuntu upgrades, go with the LTS releases.

yes, that is just what I wanted to know :-)

thanks Mr. OFB

---

### Post by ikt on 2010-10-28
> **albertwt said:**
> I'm planning to deploy Linux VM in datacenter but is there any beneftis installing the non LTS version ?


You'll want to stick with 10.04 for any servers, there is longer support and that release has a heavy emphasis on stability.

---

### Post by primaxx on 2010-10-28
Another thing to remember is that some software vendors, like for instance [Zimbra]("http://www.zimbra.com/community/"), only develop software that runs on (some of) the LTS-versions of Ubuntu.

Just my two cents... :-)

---

### Post by albertwt on 2010-10-28
> **ikt said:**
> You'll want to stick with 10.04 for any servers, there is longer support and that release has a heavy emphasis on stability.

Cool,
thanks for all of the suggestion and the explanation, I really appreciate that guys.

cheers,

Albert

---

### Post by wilsonpenha on 2010-11-09
I have a 5 years OLD DELL XPS machine, 3 months ago I've done installing Ubuntu 10.04 LTS and it work just perfect for me, 
 
When 10.10 arrives I felt so excited and decide to upgrade it, well it was the worse decision I made, my system got dead, it is now so slow, kind of some video adapter crap is taking down my machine, I tried everything I could from forums and bugs sites, nothing could make it works as it was with 10.04, 
 
Today after waste sooooo many time, I decide to reinstall 10.04 which had made me happy until 10.10, it was my nightmare bcz I work with my machine.
 
I vote for 10.04 and let people with brand new machines play with 10.10
 
good luck!

---

### Post by rjbl on 2010-11-09
Contest? Depends on what you want to do with your personal computing system.

If playing with computers tugs yer wire then migrate through every single release of Ubuntu and have fun twiddling with yer scenery. If you want to do stuff with your computer then install the latest LTS, set it all up to do exactly what you want it to do and stick with that release for as long as you need to do that kind of stuff with your computer. Ubuntu Update Manager will keep your system updated with new kernel releases, bug fixes etc. It works and it works really well.

If your functional needs for computer service don't actually change then your OS and configuration will probably be good for 3 - 10 years. Ask any Microsoft customer - most of them are happy to carry on with Win2000 or XP till the cows come home.

rjbl

---

### Post by Jirinovak on 2011-01-01
> **albertwt said:**
> yes, that is just what I wanted to know 

thanks Mr. OFB


Same for me, I needed to hear this. Thank you guys. Back a while ago I started to play with Fedora, than used 8.04 LTS, then tried 9.10. . . ??? I wish to stay with 8.04 solid as rock. And now I am on 10.04 and love it. Guess we just go with the flow and wait for 11.04 or 12.04 . . . ha, cha . . .):P

---

