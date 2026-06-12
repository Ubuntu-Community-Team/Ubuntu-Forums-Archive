---
title: "Ubuntu Versions Lifecyle"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by canjecricketer on 2009-02-23
Direct answers or links to documentation about this would be appreciated.

Here's what I'm wondering about- I've seen but not entirely understood various things about how support is offered for x amount of time after a new Ubuntu version is released. And it is apparent that new versions come out fairly often- twice a year is it? 

What I'm wondering is this- what is the general consensus on how often a person needs to update to the newest version? And can this update be done as an upgrade or is it a new install? 

What I'm getting at is this- I'm a Windows system admin at a small/med organization. If I install Ubuntu on a system, what amount of OS maintenance am I looking at? Will it be possible to just seamlessly upgrade to each successive version of Ubuntu, and is that recommended? Obviously coming from an MS background, I'm used to a new OS version being released only every several years. And for example, XP has been in use for over 8 years. Though it wouldn't be recommended, if someone wanted they could have had a system running that entire time without reinstalling the OS, and through patches and service packs, they wold be entirely up to date (like I said, in the practical world, no one really likes an 8 year old Windows installation). How does this compare to the Ubuntu experience? 

Or from a different angle- if I try to nudge users towards using Ubuntu on home computers- which I might considering how impressed I've been with Ubuntu's ease of use and stability- how hard is it going to be for your average home user to stay up to date? Are new Ubuntu versions ever loaded through the Updates features? 

Thanks for any input.

---

### Post by BDNiner on 2009-02-23
There are 2 versions of ubuntu that are released. the regular releases are every 6 months and are not supported for long. The Long Term Releases are supported for 3 years on the desktop and 5 years on the server. The last LTS version was 8.04. 

So you can only upgrade from each LTS to the next LTS. In a production environment i would not recommend upgrading to every release. Probably only upgrade when an LTS comes out.

updates are loaded through the regular update tool in ubuntu. I have had my current installation for over 2 years now. It is pretty easy to upgrade although the update servers can get bogged down around the release date.

There is a lot of maintenance when running an ubuntu system. especially if you really get into it. I have lost many nights just playing around with my installation. But not maintenance like windows installs. Once you get it up and running the way you like and it is stable. It will run forever.

---

### Post by mttman on 2009-02-23
this gives a nice table and other good information

[http://en.wikipedia.org/wiki/History_of_Ubuntu]("http://en.wikipedia.org/wiki/History_of_Ubuntu")

---

### Post by Kellemora on 2009-02-23
Hi C

I'm NOT the best person to answer this question, being a noob and all myself.

But I chose to install the LTS version of Ubuntu, in my case Hardy Heron 8.04.

The in between releases are like new things being tried out to work out the bugs, has the latest and greatest drivers for the new playtime goodies.

Although called stable, they really aren't and many things in them don't work.

LTS versions are supported for a LONG time, I think it's 6 years?  So you are still in the ballpark vs Windows releases looking at it that way.

The test versions called stable are released like every 6 months I think.
LTS versions are released like once a year in April.  Thus, 6.04, 7.04, 8.04 and the upcoming 9.04 are all LTS releases.  
I don't have to worry about upgrading from 8.04 until the 11.04 edition is released almost three years more down the road.  When they will quit providing upgrades and updates for 8.04.

Unless you're trying to get the latest toys working, there is no reason to mess with the buggy test releases.  I wouldn't doubt that 6.10 or even 7.10 was the base for the upcoming 9.04 release, placed out to get the bugs worked out and the drivers all working harmoniously together.
I wouldn't think 8.10 would become the 9.04 it has so many problems yet.
Although drivers n 8.10 may be incorporated into the 9.04 release.  I don't know how they do that for sure.

I just know that if you use an LTS release, you won't have to worry for a long long time regarding it!

Hope that helps some!

TTUL
Gary

---

### Post by lykwydchykyn on 2009-02-23
This is why there are LTS (long term support) versions -- the most recent being 8.04.  

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

They get released every two years, and enjoy security updates for three years on desktop software, and five years on server and core software.  I'd recommend that for a business setting.

I've upgraded my systems for the most part; it's pretty easy and user-friendly, but I'd be lying if I said I didn't run into glitches doing upgrades that required a little extra savvy to get through.  My approach for more important systems is to keep two partitions available for the system partition and just juggle back and forth between them every time I upgrade, so that the previous version stays intact.  Obviously not what you want in a major deployment, though.

---

### Post by matteojg on 2009-02-23
Depends on the Ubuntu build you install:

Intrepid Ibex (8.10) will be maintained by Canonical until 2010
Hardy Heron (8.04) will be maintained by Canonical until April 2011

In April 2010 Canonical will release Ubuntu 9.04 Jaunty Jackalope. 

To see how an upgrade from 8.10 to 9.04 would work (its very simple and user friendly) go to : [http://www.ubuntu.com/testing/jaunty/alpha3]("http://www.ubuntu.com/testing/jaunty/alpha3")

---

### Post by 67GTA on 2009-02-23
I would recommend staying with the long term support releases(LTS) for production machines. As stated above, they are released every three years, and can be upgraded to the new version through the update manager. The current is Hardy Heron 8.04. The next LTS will be 2011. The six month releases are not as stable because Ubuntu takes a current snapshot of Debian Sid for each six month release, and then adds the "Ubuntu Touch". Debian Sid is known to be a little buggy. Usually by the time the next LTS comes out, most of the bugs have been fixed by Debian devs, or by the Ubuntu devs. That way you can keep a stable OS with security updates for three years and update when the next LTS comes out, and not have to reinstall every six months.

---

### Post by matteojg on 2009-02-23
The dates in my previous post refer to the desktop editions...server editions are supported longer (8.04 up until 2013)...

The salient point here is that updating to a new build is very easy...and *very* cheap ;)

---

### Post by ikisham on 2009-02-23
LOL!

LTS - released each 2 years (next 10.04 - april 2010); maintained for 3 years (desktop) or 5 years (server).
Other versions - released each six months (minus when an LTS is released - next 9.04 - april this year, 2009); maintained (security patches, I think) for 1 1/2 year.

---

