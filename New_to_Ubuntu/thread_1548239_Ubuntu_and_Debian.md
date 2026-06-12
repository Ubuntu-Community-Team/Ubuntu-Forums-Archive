---
title: "Ubuntu and Debian"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by BobbyDing on 2010-08-08
Hi All,
I'm a nuwb to Linux, and have a couple questions about the relationship between Ubuntu and Debian and linux itself. I understand that Ubuntu is 'Based' on debian, but is a separate entity. I am beginning to understand the 'upstream' and 'downstream' relationship between the two. I understand that debian does rolling releases, and that ubuntu is scheduled releases. Which brings me to my first question....

I noticed that update manager in ubuntu does occasional updates (could be daily, could be weekly, etc..) as they become available. Are these the rolling releases (bug fixes) arriving from debian and being passed through canonical to my install of ubuntu? I am confused by these since canonical does scheduled releases (every 6 months), right? Or am I misunderstanding the it completely?

I'm trying to get a basic picture of how the different distros are assembled. Is debian the kernel portion? Or is linux (created by Mr. Torvalds) the kernel, and debian is a layer on top of linux? And where does ubuntu (as well as other distros based on ubuntu) fall in. Are they layered (if that's the right word) like:

linux (kernel), then debian (or ubuntu, etc..) on top of that, then the desktop (gnome, kde)?


Thanks for any assistance.

Bobby

---

### Post by jtarin on 2010-08-08
> **BobbyDing said:**
> Hi All,
I'm a nuwb to Linux, and have a couple questions about the relationship between Ubuntu and Debian and linux itself. I understand that Ubuntu is 'Based' on debian, but is a separate entity. I am beginning to understand the 'upstream' and 'downstream' relationship between the two. I understand that debian does rolling releases, and that ubuntu is scheduled releases. Which brings me to my first question....

I noticed that update manager in ubuntu does occasional updates (could be daily, could be weekly, etc..) as they become available. Are these the rolling releases (bug fixes) arriving from debian and being passed through canonical to my install of ubuntu? I am confused by these since canonical does scheduled releases (every 6 months), right? Or am I misunderstanding the it completely?

I'm trying to get a basic picture of how the different distros are assembled. Is debian the kernel portion? Or is linux (created by Mr. Torvalds) the kernel, and debian is a layer on top of linux? And where does ubuntu (as well as other distros based on ubuntu) fall in. Are they layered (if that's the right word) like:

linux (kernel), then debian (or ubuntu, etc..) on top of that, then the desktop (gnome, kde)?


Thanks for any assistance.

BobbyUbuntu and Debian share the same package management system, but use different repositories of software.All Linux distributions share the Linux kernel, some distros more recent kernels than others.
Kernels take some time to prove themselves and to have all the possible bugs worked out and all the possible configurations and support for the newest hardware possible, so it goes with versions of software that try to keep pace with all of this.Some distros are known as bleeding-edge, some as more stable than others.Each release is supposed to be an improvement over the last.Most of the update notifications you get are security and bug fixes....all software has dependencies on other software. So its a constant growing thing.
Think of the distro as an entity the provides the relationship between the kernel and the desktop...such as Gnome,KDE etc.

---

### Post by Doobie9 on 2010-08-08
Linux itself is the kernel: [http://kernel.org/](http://kernel.org/) . The rest of the operating system comes from GNU and various other sources. It's a very modular operating system.

As for the differences between Debian and Ubuntu (I use both, in addition to Mint), I find that Ubuntu tends to be much 'edgier' and sort of changes the system around somewhat (such as the use of upstart instead of init). Debian, in my experience, has fewer quirks to it. Ubuntu is somewhat easier (though Debian isn't at all difficult). Once you get past the non-gui install (which is much easier than it sounds), and get booted to a desktop, Debian is pretty easy (although it is somewhat more complicated to get stuff like proprietary drivers and whatnot, or at least it has been in my experience--someone else's experience may have been different from my own). I tend to choose Debian for something I'm not going to be able to maintain a lot; like if someone wanted a dedicated web/openoffice kiosk sort of thing. Ubuntu I like for more general desktop-orientated use. Say, for example, if someone were going to install lots of software or play games in wine--there are just more resources online for someone new to find their way around Ubuntu; such as this forum, for example.

They're different branches of the same tree. Or, to put it another way, Debian is a sort of conservative 'father knows best' distro and Ubuntu is the radical teenage son who gets tattoos and plays that darn Rock & Roll music too loud :P. 

Yea, that's kind of a gross exaggeration, but I hope you get the gist of it ;).

---

### Post by cascade9 on 2010-08-08
> **BobbyDing said:**
>  I understand that debian does rolling releases, and that ubuntu is scheduled releases. Which brings me to my first question....

Well, sort of....Ubuntu does only scheduled releases (on a hard timetable that AFAIK has only been out once, with 6.06). Debian does have rolling releases- 'testing', currently 'squeeze' and 'unstable', which is always 'sid'. But the main version of debian, 'stable', currently 'lenny' is not rolling release. The packages are tested on unstable, then after some testing, etc, move down to 'testing'. Every now and again, testing goes into a freeze (when no new features, program updates, etc are moved in) and once is it considered stable, it becomes the new stable version of debian. Keeping its codename. Since squeeze has just moved into a freeze (on 06-08-2010), in a few months, maybe up to a year, squeeze will become the new stable release.

BTW, the codenames for debian are based on toy story, and Sid is the kid who breaks toys. ;)

---

### Post by The Cog on 2010-08-08
Both Debian and Ubuntu are full distros. Ubuntu is basically taking Debian and making minor usability changes.

---

