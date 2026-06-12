---
title: "Firefox 3.5 in Jaunty"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by methodmarvel on 2009-06-23
When firefox 3.5 is released will it come as an update for 9.04 users or will we need to install the new version from the firefox website?

---

### Post by halitech on 2009-06-23
only bug fixes and critical updates are done once a version has been released so if you want 3.5 you'll need to install it yourself.

---

### Post by methodmarvel on 2009-06-23
> **halitech said:**
> only bug fixes and critical updates are done once a version has been released so if you want 3.5 you'll need to install it yourself.

Thanks - I believe you but I'm confused.

3.5 isn't critical? I know it's mostly about new features but surely any new security fixes mozilla make will only be applied to 3.5 not the 3.0.+ series? Isn't the 3.0.+ series going to be unsupported by mozilla after 3.5 release?

---

### Post by Mornedhel on 2009-06-23
Hello,

Firefox 3.5 "Shiretoko" is already available in the repositories. Just install the firefox-3.5 package, it will replace the current stable 3.1.

---

### Post by bennachie on 2009-06-23
You'll have several ways to install the stable version of Firefox 3.5, but you would probably be better to do so from a third-party repository rather than downloading a .deb package (using a repository gives you a reasonable chance of keeping up with security updates and the like). 

Google will be your friend.

---

### Post by halitech on 2009-06-23
> **methodmarvel said:**
> Thanks - I believe you but I'm confused.

3.5 isn't critical? I know it's mostly about new features but surely any new security fixes mozilla make will only be applied to 3.5 not the 3.0.+ series? Isn't the 3.0.+ series going to be unsupported by mozilla after 3.5 release?

I'm not sure about the support part of things but if any app releases a new version, unless it fixes some critical bug in the version in the repo, it doesn't get added until the next release. This keeps things on an even keel and allows the devs to test it before including it as the de facto standard.

As others have said, it seems 3.5 is in the repos so they must have tested it enough to add it in the middle of a release.

---

### Post by methodmarvel on 2009-06-23
> **Mornedhel said:**
> Hello,

Firefox 3.5 "Shiretoko" is already available in the repositories. Just install the firefox-3.5 package, it will replace the current stable 3.1.

3.1 = 3.5 I believe - they simply renamed it due to the features developed for acurate description. 

Stable at the moment is 3.0.11 which has been updated through the ubuntu repos.

I was wondering if 3.0.11 > 3.5 via ubuntu updates alone. Apparently it wont and now I'm wondering about security fixes -if mozilla will produce them for 3.0.11 as it's soon replaced by 3.5

The 3.5 in the repos is beta4 - but this obviously isn't getting updated as we're upto 3.5rc2 on the firefox 3.5 website.

---

### Post by methodmarvel on 2009-06-23
> **bennachie said:**
> You'll have several ways to install the stable version of Firefox 3.5, but you would probably be better to do so from a third-party repository rather than downloading a .deb package (using a repository gives you a reasonable chance of keeping up with security updates and the like). 

Google will be your friend.
Hard to trust a third party repo.

---

### Post by Joeb454 on 2009-06-23
I don't think 3.5 will get into Jaunty via the official repo's. There is a small chance it may go through backports, though I don't expect it to.

What will most likely happen is somebody will put it into a PPA on launchpad, which you can then add to your sources.list and install it that way :)

---

### Post by methodmarvel on 2009-06-23
> **Joeb454 said:**
> I don't think 3.5 will get into Jaunty via the official repo's. There is a small chance it may go through backports, though I don't expect it to.

What will most likely happen is somebody will put it into a PPA on launchpad, which you can then add to your sources.list and install it that way :)

Thanks.

It's a shame ubuntu guys wont package it. I wish ubuntu was more of a rolling release type thing - Install it once and it updates releases (eg 7.04>7.10) and software to the most recent *stable* versions (firefox 3.0.11>3.5). That's my idea of the ideal linux distro.

I understand that would be more difficult - and imposible to impliment a new file system ontop of a installed system eg ext3>ext4 but it would be an amazing seamless experience.

---

### Post by Mornedhel on 2009-06-23
If you use the security and backports repositories, Shiretoko should get updated when needed. Beta to release transitions should qualify for an update, I think.

If you need a rolling release distribution, you could try Debian unstable.

---

### Post by halitech on 2009-06-23
> **Mornedhel said:**
> 
If you need a rolling release distribution, you could try Debian unstable.

wouldn't even need to use unstable, I use Debian testing and as long as the repo is set up using testing(or stable/unstable/sid) instead of the code name (etch/lenny/squeeze) then it will update things as it goes along.

PS. I wouldn't suggest stable if you want current releases as it is called stable for a reason and the apps are on the older side

---

### Post by methodmarvel on 2009-06-23
> **Mornedhel said:**
> If you use the security and backports repositories, Shiretoko should get updated when needed. Beta to release transitions should qualify for an update, I think.

If you need a rolling release distribution, you could try Debian unstable.

Problem with debian unstable - it's unstable right? I mean it's going to break frequently, isn't it?

Is the backports repo just ticking a box in the software sources under the update tab?

---

### Post by methodmarvel on 2009-06-23
> **halitech said:**
> wouldn't even need to use unstable, I use Debian testing and as long as the repo is set up using testing(or stable/unstable/sid) instead of the code name (etch/lenny/squeeze) then it will update things as it goes along.

PS. I wouldn't suggest stable if you want current releases as it is called stable for a reason and the apps are on the older side

But is 3.5 unstable? I think the descriptors are confusing me. I mean how much testing to the ubuntu guys do of a new firefox release say when they're looking to put 3.5 into 9.10?

---

### Post by Joeb454 on 2009-06-23
> **methodmarvel said:**
> Is the backports repo just ticking a box in the software sources under the update tab?

It is indeed.

There are many rolling release distro's you can try out if you feel you would prefer it. I believe Arch is rolling release, as is Gentoo. I can't think of any others off the top of my head, and I know both of those can sometimes be a pain to set up ;)

---

### Post by Mornedhel on 2009-06-23
> **methodmarvel said:**
> Problem with debian unstable - it's unstable right? I mean it's going to break frequently, isn't it?

It has stability issues, yes. As halitech says, you may want to use testing instead. Depends on your preferred ratio of bleeding-edge/stability. Unstable does break sometimes, but not that frequently. (Debian releases are named after Toy Story characters ; unstable is always called "Sid", the kid who likes breaking toys.) Testing is as stable as Ubuntu. Stable is server-grade stuff, which means security updates only.

> **methodmarvel said:**
> Is the backports repo just ticking a box in the software sources under the update tab?

That's right.

---

### Post by halitech on 2009-06-23
> **methodmarvel said:**
> Problem with debian unstable - it's unstable right? I mean it's going to break frequently, isn't it?

I haven't used unstable but with testing, even though its supposed to be testing I find it is more stable then my old windows 2000 install after 4 service packs :)

> **methodmarvel said:**
> But is 3.5 unstable? I think the descriptors are confusing me. I mean how much testing to the ubuntu guys do of a new firefox release say when they're looking to put 3.5 into 9.10?

there is a new release every 6 months but I'm sure even though 9.10 is the next release that they are working on 10.04 and deciding what is going to be included so they probably work on it for close to a year before it is released. I stand to be corrected though if I'm wrong.

---

### Post by methodmarvel on 2009-06-23
So if I moved to Debian testing what do you think my main problems would be?


I tried to install debian before but had some issues with the small cd install (net install?). I didn't try the huge list of 30CDs though - I read you only have to install disk 1? It's not clear like ubuntu is.

Also - no ubuntu-restricted-extras package which I'd miss.

---

### Post by halitech on 2009-06-23
> **methodmarvel said:**
> So if I moved to Debian testing what do you think my main problems would be?


I tried to install debian before but had some issues with the small cd install (net install?). I didn't try the huge list of 30CDs though - I read you only have to install disk 1? It's not clear like ubuntu is.

Also - no ubuntu-restricted-extras package which I'd miss.

hard to say if you would have any issues

I use either the net install or the full xfce+lxde cd

testing cd - [http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/](http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/)

netinstall - [http://cdimage.debian.org/debian-cd/5.0.1/i386/iso-cd/debian-501-i386-netinst.iso](http://cdimage.debian.org/debian-cd/5.0.1/i386/iso-cd/debian-501-i386-netinst.iso)

for multimedia, you would just need to add the debian-multimedia repo and then you can install w32codecs

---

### Post by methodmarvel on 2009-06-23
> **halitech said:**
> hard to say if you would have any issues

I use either the net install or the full xfce+lxde cd

testing cd - [http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/](http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-cd/)

netinstall - [http://cdimage.debian.org/debian-cd/5.0.1/i386/iso-cd/debian-501-i386-netinst.iso](http://cdimage.debian.org/debian-cd/5.0.1/i386/iso-cd/debian-501-i386-netinst.iso)

for multimedia, you would just need to add the debian-multimedia repo and then you can install w32codecs

w32codecs include lame for mp3 decoding/encoding?

I'm installing on a laptop (info in signature).

Do problems in testing end up getting fixed by updates or would I need to fix them myself?

---

### Post by halitech on 2009-06-23
> **methodmarvel said:**
> w32codecs include lame for mp3 decoding/encoding?

I'm installing on a laptop (info in signature).

Do problems in testing end up getting fixed by updates or would I need to fix them myself?

its been so long since I did my install that I honestly don't remember if lame was in debian-multimedia or the main debian repo.

looks like the x300 video card should work after installing the proprietary driver. Sound should work as well. The output of ```
lshw
``` wil give us a better idea of your hardware

some things you'll need to edit some conf files to fix but most things will be resolved with updates

---

### Post by Mornedhel on 2009-06-23
Since this thread has been hijacked towards a discussion on Debian, I will admit that I've been considering moving to Debian as well. Unfortunately, my ethernet port is physically borked, and I'm a bit worried that the wireless might not be working out of the box.

halitech: Do you know if an Intel 3945 wireless chipset is supported, and should I try the netinstall image, or should I rather use the weekly build images ? I am quite comfortable with the command line and routinely use the terminal for about everything, but the one problem with Ubuntu automagically configuring everything is that you end up not really knowing what works how and where.

Also, what is the state of proprietary video drivers on Debian ?

---

### Post by halitech on 2009-06-23
> **Mornedhel said:**
> Since this thread has been hijacked towards a discussion on Debian, I will admit that I've been considering moving to Debian as well. Unfortunately, my ethernet port is physically borked, and I'm a bit worried that the wireless might not be working out of the box.

halitech: Do you know if an Intel 3945 wireless chipset is supported, and should I try the netinstall image, or should I rather use the weekly build images ? I am quite comfortable with the command line and routinely use the terminal for about everything, but the one problem with Ubuntu automagically configuring everything is that you end up not really knowing what works how and where.

Also, what is the state of proprietary video drivers on Debian ?

the intel card seems to be supported but does not work without installing the binary blob to get it working which means you need a wired connection first. Do you have a spare PCI slot where you could pop in a wired card for the install?

Debian is not as hard as people try to make it sound. I started using Ubuntu around 6.06 and then changed to debian around a year ago. I feel ubuntu gave me a good grasp on what I was getting into and in my mind, if you can install and use ubuntu, you can install and use debian.

Video drivers are in good shape right now. ATI has dropped support for some older cards but I have an onboard X1200 and the binary driver worked fine and installed with no issues. Not sure on Nvidia but I think the newest ones are working great as well.

---

### Post by Mornedhel on 2009-06-23
> **halitech said:**
> the intel card seems to be supported but does not work without installing the binary blob to get it working which means you need a wired connection first. Do you have a spare PCI slot where you could pop in a wired card for the install?

No, it's a laptop. I don't really want to poke inside since it's the machine I use everyday for work. I can get by with a live CD if I break something since all I really need if it comes to the worst is ssh to another box on which I have an account and emacs is installed.

> **halitech said:**
> Debian is not as hard as people try to make it sound. I started using Ubuntu around 6.06 and then changed to debian around a year ago. I feel ubuntu gave me a good grasp on what I was getting into and in my mind, if you can install and use ubuntu, you can install and use debian.

I started with a Mandrake -- yes, when it was still called Mandrake -- before that, but didn't really use it ; and before that I managed to install a Red Hat -- yes, when it was still called Red Hat -- which didn't really work at all. I was young then and since my primary use for a computer was gaming, nothing really came out of it. Then a few years later I heard about this Debian derivative that was user friendly, and when I installed Dapper Drake it just worked.

I don't expect Debian to be especially hard, but consider for instance the wireless : every Ubuntu release since at least Hardy Heron supported my wireless chipset, and every Ubuntu release since at least Dapper Drake supported my previous machine's wireless. Ubuntu does make the process easier on newcomers. Although I have come to a good understanding of the superficial workings (hey, I code in Perl and use emacs) I can't really say for instance that I would know how to configure the wireless without NetworkManager. Installing Debian is probably a good way to force myself to learn a bit more.

> **halitech said:**
> Video drivers are in good shape right now. ATI has dropped support for some older cards but I have an onboard X1200 and the binary driver worked fine and installed with no issues. Not sure on Nvidia but I think the newest ones are working great as well.

Right. I have an NVidia 8400M GS. If the binary blobs exist for Ubuntu, they probably exist for Debian somewhere. As I said, if I have a command line available then I can work around most things.

I will see if I can find the drivers for my wireless before I attempt the installation.

---

### Post by halitech on 2009-06-23
> **Mornedhel said:**
> No, it's a laptop. I don't really want to poke inside since it's the machine I use everyday for work. I can get by with a live CD if I break something since all I really need if it comes to the worst is ssh to another box on which I have an account and emacs is installed.

yeah, guess it is hard to put a wired nic in a laptop

> I started with a Mandrake -- yes, when it was still called Mandrake -- before that, but didn't really use it ; and before that I managed to install a Red Hat -- yes, when it was still called Red Hat -- which didn't really work at all. I was young then and since my primary use for a computer was gaming, nothing really came out of it. Then a few years later I heard about this Debian derivative that was user friendly, and when I installed Dapper Drake it just worked.

I played around with Mandrake and redhat as well back in 2000 and it was murder to try and set it up. Ubuntu adds a lot of extras to make things easier.

> I don't expect Debian to be especially hard, but consider for instance the wireless : every Ubuntu release since at least Hardy Heron supported my wireless chipset, and every Ubuntu release since at least Dapper Drake supported my previous machine's wireless. Ubuntu does make the process easier on newcomers. Although I have come to a good understanding of the superficial workings (hey, I code in Perl and use emacs) I can't really say for instance that I would know how to configure the wireless without NetworkManager. Installing Debian is probably a good way to force myself to learn a bit more.

wireless is the one area where linux is falling behind in the usability area that ubuntu is a little ahead of the rest. Hopefully it will continue to get better as time goes by.

> Right. I have an NVidia 8400M GS. If the binary blobs exist for Ubuntu, they probably exist for Debian somewhere. As I said, if I have a command line available then I can work around most things.

I will see if I can find the drivers for my wireless before I attempt the installation.

hopefully you can grsb them, put them on a thumbdrive and then install them but I don't use much wireless and mine just worked on the one laptop I use.

---

### Post by lovinglinux on 2009-06-24
I was also expecting to get Firefox 3.5 final on Jaunty, but it seems that I will be using [Swiftfox](http://getswiftfox.com/index.htm) instead, from now on. You can install Swiftfox from it's own [repository](http://getswiftfox.com/deb.htm). Swiftfox uses the most recent version of Firefox and it is installed side-by-side with it. Nevertheless, it uses the same profiles as Firefox.

---

### Post by bhadotia on 2009-06-24
> **Joeb454 said:**
> It is indeed.

There are many rolling release distro's you can try out if you feel you would prefer it. I believe Arch is rolling release, as is Gentoo. I can't think of any others off the top of my head, and I know both of those can sometimes be a pain to set up ;)


Sabayon is rolling release (being based on gentoo) and has many non-free software such as codecs etc. available from the install DVD itself (including many other cool free stuff such as games etc.). 
But if you want to install it from the DVD make sure you have a free partition of at-least 12 Gigs as DVD installer is, well, stupid :D and install every thing that it has even though you surely would not need all the software present on the DVD.

---

### Post by snkiz on 2009-06-24
pardon me for being on topic, but in the past when Firefox has been updated to a new version, the old one continues to get security upgrades for a while at least. Since Firefox for jaunty was stable when released it will only get security updates and 3.5 is a separate package. If Ubuntu sticks to what they've done before 3.5 will be in karmic as long as its close enough, and be upgraded to stable when it becomes available

---

### Post by woodstokcurly on 2009-06-30
> **snkiz said:**
> pardon me for being on topic, but in the past when Firefox has been updated to a new version, the old one continues to get security upgrades for a while at least. Since Firefox for jaunty was stable when released it will only get security updates and 3.5 is a separate package. If Ubuntu sticks to what they've done before 3.5 will be in karmic as long as its close enough, and be upgraded to stable when it becomes available
Firefox 2.0.x has only just stopped being supported. It was supported for a long time even though Firefox 3.0.x was available. Firefox 3.0.x will continue to be supported up until the next release after Firefox 3.5, if we go by what happened with Firefox 2.0.x

It is true that Ubuntu likes to "freeze" the software packages for each version (that's why they have "package freezes" etc. in the development process) and only include stability and security updates. A limited number of minor backports can be installed separately via enabling the Backports channel, but this is very limited. For example, OpenOffice.org 3.1 was not available in the Backports channel and it is unlikely that Firefox 3.5 will be, for Jaunty and earlier that is.

And so it has been for a while, if Ubuntu users want the latest and greatest then they have to add extra repositories and hope for the best, by understanding that they are installing software that is unsupported by Canonical for that particular version. Firefox 3.5 will most definately be included in Karmic Koala.

---

### Post by colau on 2009-08-15
Easiest way to install firefox-3.5!
[psychocats]("http://www.psychocats.net/ubuntu/firefox")

---

