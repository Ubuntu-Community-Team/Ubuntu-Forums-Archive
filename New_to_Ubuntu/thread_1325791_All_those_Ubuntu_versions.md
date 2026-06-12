---
title: "All those Ubuntu versions"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by sfxpt on 2009-11-13
Hi, 

Coming from the Debian background, in which only 3 versions are available (stable, testing and unstable), Ubuntu has way too many versions for me to choose. So far everything are still confusing to me. E.g., 

- what's the deference between 8.04 & 8.10?
- what's the deference between 9.xxx?
- how current the casper be for Ubuntu 8.04 or 8.10?
- how about other app, say checkgmail or fetchyahoo, does Ubuntu have them; how current they are in Ubuntu 8.04 or 8.10?

I'm wondering if there is any where I can see detailed explanation about Ubuntu versions from the package versions prospective, and compare them with Debian versions. 

So far I only found one, Posted August 11, 2009 by corbet, but it's on Debian/Ubuntu versions that way too old for me:

**[SIZE=3]Debian Etch and Ubuntu Feisty: a comparison[/SIZE]**

[http://lwn.net/Articles/346400/](http://lwn.net/Articles/346400/)


    etch: froze in December 2006, released in April 2007; still supported
    feisty: DebianImportFreeze in Dec 2006, UpstreamVersionFreeze in Feb 2007,
        released in April 2007; support ended October 2008

***EDIT*:** Thanks everyone for the replies, especially to Marlonsm, jmszr & markbuntu. I've skimmed through the "Free Beginners Guide", which clear up many other questions. But still there's one more:

From the package repository prospective, what's the different between the Desktop Edition and the Server Edition? Don't they share the same packages, same 
versions? Will the /etc/apt/sources.list file be different between the Desktop Edition and the Server Edition? If not, then does it really matters that the Desktop Edition of Dapper Drake has reached EOL while the Server Edition is supported until June 2011?

thanks

sfxpt

---

### Post by Spiritof76 on 2009-11-13
The current version is at 9.10, the higher the number the newer and better it is.  8.04 is prommised long term support. but I just keep upgrading every 6 months to get the newer and better features

---

### Post by brandonsh on 2009-11-13
> **Spiritof76 said:**
> The current version is at 9.10, the higher the number the newer and better it is.  8.04 is prommised long term support. but I just keep upgrading every 6 months to get the newer and better features
Exactly that. I'm currently on 9.04 though, and it works fine. My 9.10 disks are in the mail! :D

---

### Post by kansasnoob on 2009-11-13
You can't Google?

[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases)

---

### Post by J-Buntu on 2009-11-13
Go with a supported version and check how long it will be supported for, maybe try a couple virtually, or with Wubi - and see for yourself which works better for you. Jaunty worked near perfectly for me and Karmic is better, but needed a few more tweaks to make things work on my machine, i think it all depends on your computer really.
______________________

HP dv6910ea
Intel Core 2 duo 2Ghz
NVIDIA GeForce 8400M GS
3Gib RAM
______________________

---

### Post by kansasnoob on 2009-11-13
I guess I should say that I've found 9.10 terribly unstable! The worst I've seen since I found Ubuntu nearly a year ago.

Karmic has been like the Sidux of Ubuntu!

---

### Post by Marlonsm on 2009-11-13
The number of the release refers to when it was released (year.month). The current one, for example was released in October 2009, so it's 9.10.
There is a new release every six months (one in April and one in October). Every two years there is the LTS (long term support) release.
A normal release is supported for 18 months, and a LTS is supported for 3 years in desktops and 5 years in servers.

And there is the naming. It goes in alphabetical order (except the first 3 releases), and is always an Adjective + Animal name, the current one is Karmic Koala, the next one is Lucid Lynx.

Besides that, there are all the alphas and betas before the releases.

The current release is 9.10 Karmic Koala and the current LTS is 8.04 Hardy Heron. And soon there will be pre-release versions of the next LTS, 10.04 Lucid Lynx.

---

### Post by rmockler on 2009-11-13
Excellent Marlonsm, perfect answer to what the guy asked.

---

### Post by Zoot7 on 2009-11-13
Just to add the version number is nothing more than the month of release and year of release.
eg Hardy was released in April 2008, so hence 8.04.
Sames goes with the other releases too.

---

### Post by jmszr on 2009-11-13
sfxpt,

This should help with your casper question: [http://packages.ubuntu.com/search?keywords=casper](http://packages.ubuntu.com/search?keywords=casper) .

Ubuntu release packages: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Hope that helps.

---

### Post by stormvinyl on 2009-11-13
I had the same questions.  If you look at the "Free Beginners Guide" it will answer all your questions.  It talks about all the different versions, why they use the numbers, different then you would expect. and what to expect from Ubuntu.  Its really a good read and definitely a must read prior to using Ubuntu.

---

### Post by markbuntu on 2009-11-13
If you are coming from Debian, Ubuntu 8.04 is closest to Debian stable as far as kernel and application versions etc. 9.04 is closest to testing and 9.10 closest to unstable but unstable will be moving ahead soon and testing will be moving closer to 9.10 in the next few months. 

Many of the packages used in ubuntu come directly from the Debian testing and unstable repos and many bug fixes also come from Debian.

---

### Post by sfxpt on 2009-11-13
Thanks everyone for the replies, especially to Marlonsm, jmszr & [markbuntu]("http://ubuntuforums.org/member.php?u=566591").

---

### Post by pablolie on 2009-11-14
i run different versions on different machines. the candidates these days are

8.04 LTS - i think this should be your main bet if you are in IT and provisioning systems for other people that you want to make sure work. it is proven.

9.04 is still supported, and works well. the user interfaces is a tad sleeker than 8.04, wireless a tad more self-configuring. i run 9.04 on my always-on home machine.

9.10 is the latest and greatest. works well, but i just run it on non-critical machines to gather experience with it. i don't find the progress significant enough to incur the risk to migrate my always on machine.

10.04 is several months off, but it is probably what i will wait for before i upgrade my main machine. and then stick with it for a while, since it is the next LTS that will incorporate all of the sleeker 9.10 features.

---

