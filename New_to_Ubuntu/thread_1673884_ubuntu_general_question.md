---
title: "ubuntu general question"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by daveboy23 on 2011-01-23
hi guys,
i've been thinking - as far as i understand - ubuntu is the kernel from one source, gnome from another, xorg, apps etc.  so basically, everything is made separately and then joined together.
if this is true (or maybe i'm really wrong) why do you need to update (say for 11.04)? i can just get the updates and be happy... get the kernel, get the gnome, everything one by one.

---

### Post by cavh on 2011-01-23
Close, but not quite. The Linux kernel is the operating system proper and is used by Ubuntu, Debian, Fedora, Red Hat and all other Linux distributions. See [http://kernel.org]("http://kernel.org") and [http://en.wikipedia.org/wiki/Linux_kernel]("http://en.wikipedia.org/wiki/Linux_kernel").

Gnome, the various applications which one can run on it (and on other desktop managers, like KDE) are provided by other organisations; including Canonical, which sponsors Ubuntu development and owns the Ubuntu trademarks.

Moving from say Lucid (10.04) to Maverick (10.10) is called an upgrade, not an update. There is no need as such to do an upgrade unless you need extended support. The releases with '.04' in the name are supported by Canonical for 18 months or 24 months (not quite sure which), the ones with '.10' in the name are supported for three years on the desktop and five on the server. These are called LTS releases (LTS means long term support). See [https://wiki.ubuntu.com/LTS]("https://wiki.ubuntu.com/LTS")

---

### Post by ubudog on 2011-01-23
> **cavh said:**
> Close, but not quite. The Linux kernel is the core of the operating system and is used by Ubuntu, Debian, fedora, RedHat and all other Linux distributions. See [http://kernel.org]("http://kernel.org").

Gnome, the various applications which one can run on it (and other desktop managers, like KDE) are provided by other organisations, including Canonical, which sponsors Ubuntu development.

Moving from say Lucid (10.04) to Maverick (10.10) is called an upgrade, not an update. There is no need as such to do an upgrade unless you need support beyond two years (for non-LTS releases, LTS means long term support). The release with '.04' in the name are supported by Canonical for 18 months or 24 months (not quite sure which), the ones with '.10' in the name are supported for three years on the desktop and five on the server. See [https://wiki.ubuntu.com/LTS]("https://wiki.ubuntu.com/LTS")

Great explanation.  :-)

---

### Post by Hur Dur on 2011-01-23
TL;DR: Linux is a kernel. GNOME is a desktop environment that has been around for a long time. Ubuntu is a distribution based on Linux using the GNOME environment.

---

### Post by mastablasta on 2011-01-23
> **cavh said:**
> The releases with '.04' in the name are supported by Canonical for 18 months or 24 months (not quite sure which), the ones with '.10' in the name are supported for three years on the desktop and five on the server. These are called LTS releases (LTS means long term support). See [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

are you sure? 10.04 means the date of edition year 2010, april (4th months). 
only the edition with LTS in it has support for 3 years and not any edition with .04 in it which just means it goes out in april. Natty 11.04 will not be supported for 3 years (desktop).

---

### Post by daveboy23 on 2011-01-23
so if i'm getting you right, i can stay with my 10.10 for the next 3 years and still be with the latest software, kernel etc. (running updates all the time) and an "upgrade" is nothing more then putting all the new kernel, software and stuff into a CD and giving it a new name?
is that correct? or am i missing something?

---

### Post by kaldor on 2011-01-23
> **mastablasta said:**
> are you sure? 10.04 means the date of edition year 2010, april (4th months). 
only the edition with LTS in it has support for 3 years and not any edition with .04 in it which just means it goes out in april. Natty 11.04 will not be supported for 3 years (desktop).

Yep.

Longterm Support Releases are once every 2 years. Currently, there are 3; 6.06, 8.04 and 10.04.

The 10 is just Ubuntu's release month.

6.06 = Ubuntu 2006, June (06/06)
10.04 = Ubuntu 10th year, 4th Month (2010, April)
10.10 = Ubuntu 2010, October (10/10)

The .04 or .10 have nothing to do with LTS.

> so if i'm getting you right, i can stay with my 10.10 for the next 3 years and still be with the latest software, kernel etc. (running updates all the time) and an "upgrade" is nothing more then putting all the new kernel, software and stuff into a CD and giving it a new name?
is that correct? or am i missing something?

No, that would be with Ubuntu 10.04; the other poster was mistaken.

---

### Post by Timmer1240 on 2011-01-23
If you want the latest all the time I would install Linux mint debian which updates all the time is a rolling release never have to reinstall I wish ubuntu would do that 10.10 is only supported for 18 months after its released so its not 3 years.Im gonna repartion and install LMDE alongside xp and Ubuntu and give that aspin for a while like the sound of it myself!

---

### Post by Paqman on 2011-01-23
> **daveboy23 said:**
> why do you need to update (say for 11.04)? i can just get the updates and be happy... get the kernel, get the gnome, everything one by one.

Because the repositories won't have the required updates in them. Ubuntu uses fairly stable repositories. Once a version is released, the versions of packages in the repos don't change much. Normally only security updates and major bugfixes are added to the repos. To get updated versions of Gnome, the kernel, xorg, etc then you'd need to jump to the newer version.

There are exceptions to this. Some packages get backported to older versions, so if you enable the backports repo you'll get those. There is also the option of using PPAs to get new packages into an old version. But generally, if you want the latest packages, you need to be running the latest version.

---

### Post by Chris Edgell on 2011-01-23
I wish someone would state this one time clearly.  At least it's still not clear to me...

Is 10.04 Lucid Lynx LTS?

Is 10.10 LTS?

I thought every three years there is a new release that, again, IS Long Term Support.  Is it every two years?

---

### Post by ubudog on 2011-01-23
> **Chris Edgell said:**
> I wish someone would state this one time clearly.  At least it's still not clear to me...

Is 10.04 Lucid Lynx LTS?

Is 10.10 LTS?

I thought every three years there is a new release that, again, IS Long Term Support.  Is it every two years?

10.04 - LTS
10.10 - Not LTS

---

### Post by Zill on 2011-01-23
> **Chris Edgell said:**
> I wish someone would state this one time clearly.  At least it's still not clear to me...

Is 10.04 Lucid Lynx LTS?

Is 10.10 LTS?

I thought every three years there is a new release that, again, IS Long Term Support.  Is it every two years?
[Ubuntu Wiki LTS]("https://wiki.ubuntu.com/LTS")
[URL="http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases"]
Ubuntu (operating system)[/URL]
[URL="http://en.wikipedia.org/wiki/List_of_Ubuntu_releases"]
List of Ubuntu releases[/URL]

---

### Post by Chris Edgell on 2011-01-23
VERY good!  Thanks.

---

### Post by ubudog on 2011-01-23
> **Chris Edgell said:**
> VERY good!  Thanks.

Lol.  Cool.

---

### Post by daveboy23 on 2011-01-24
great stuff.  you see, the reason i asked is because i don't want to (or "upgrade") every 6 months.  i just want a stable release that gets updates all the time (and if i have to - reinstall the system every couple of years)

so thank you guys for clearing that up.  i will not be upgrading to 11.04, unless we want to open a new thread here called - why you should upgrade to 11.04 :-)

---

### Post by cascade9 on 2011-01-24
> **daveboy23 said:**
> great stuff.  you see, the reason i asked is because i don't want to (or "upgrade") every 6 months.  i just want a stable release that gets updates all the time (and if i have to - reinstall the system every couple of years)

Once a version of ubuntu has been released (as 'final', not an alpha or beta) you tend to only get security updates, not newer versions of programs etc..

---

### Post by mastablasta on 2011-01-24
> **daveboy23 said:**
> great stuff. you see, the reason i asked is because i don't want to (or "upgrade") every 6 months. i just want a stable release that gets updates all the time (and if i have to - reinstall the system every couple of years)
 
so thank you guys for clearing that up. i will not be upgrading to 11.04, unless we want to open a new thread here called - why you should upgrade to 11.04 :-)
 
also if you are using 10.10 now you will have 1,5 year support for it. means about until april 2012.
 
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)
 
[IMG]http://upload.wikimedia.org/wikipedia/en/timeline/1d2c08a5721fe5f8dca8aa963dc9e00a.png[/IMG]

---

### Post by mastablasta on 2011-01-24
> **Timmer1240 said:**
> If you want the latest all the time I would install Linux mint debian which updates all the time is a rolling release never have to reinstall I wish ubuntu would do that 10.10 is only supported for 18 months after its released so its not 3 years.Im gonna repartion and install LMDE alongside xp and Ubuntu and give that aspin for a while like the sound of it myself!
 
 
yeah i hear it works nice now. but what happens when debians goes back to "unstable" (testing or whatever they call it) when they prepares it for version 7?

---

### Post by cascade9 on 2011-01-24
> **Timmer1240 said:**
> If you want the latest all the time I would install Linux mint debian which updates all the time is a rolling release never have to reinstall I wish ubuntu would do that 10.10 is only supported for 18 months after its released so its not 3 years.Im gonna repartion and install LMDE alongside xp and Ubuntu and give that aspin for a while like the sound of it myself!

Debian 'testing' (or LMDE which is based on debian testing) wont have 'the latest and greatest'. Debian sid (unstable) comes closer. 

The main advantage to debian testing is rolling release. For a lot of users, that would also be a weakness. 

> **mastablasta said:**
> yeah i hear it works nice now. but what happens when debians goes back to "unstable" (testing or whatever they call it) when they prepares it for version 7?

Not much will happen. There should be more updates coming down the line, but thats about it.

---

