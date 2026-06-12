---
title: "Want to try linux again"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by an4rew on 2010-06-11
I must say the linux community have done some great work, Ubuntu looks very slick!

Should a new user to Ubuntu install the latest distro or the older releases more stable and would i be missing out on anything worthwhile?

I have 6GB ram, is x64 Linux much better than it used to be?

Thanks.

---

### Post by Afkpuz on 2010-06-11
Generally, each successive distribution should (in theory) work better than the last.  It's only if you're using cutting edge hardware that support might be worse, but that's because of drivers.

Try the latest.  I highly recommend it

---

### Post by Penguin Guy on 2010-06-11
10.04 is quite stable, but try 9.10 if you want to play it safe. I use x86_64 and everything seems to work just fine - I'd strongly advise it to get your full 6GBs of RAM.

---

### Post by VeeDubb on 2010-06-11
Two big questions there.

1. Should you try the latest and greatest or an older more stable version.

In general, that's a tough call, but since the latest and greatest version of Ubuntu is a "long term service" version, that seems like the best choice, so I'd go with 10.04

2. Is 64bit linux much better?

YES!  If you mean, "is it better than it was the last time you tried linux" then it's a resounding yes.

YES!  If you mean, "is it better than 32 bit for somebody who has 6GB of RAM, then it's a resounding yes.

64bit is the way all home computing is going, and it's going there pretty quickly.  Over the last couple of years, 64 bit linux has progressed by leaps and bounds, to the point where virtually everything is available in native 64bit, including Sun Java, and Adobe Flashplayer.  On an interesting side note, Adobe has remove the 64bit flashplayer 10 beta from their site, and refuses to comment on whether or not that means a 64bit version of 10.1 is coming soon.  In the mean time, 32bit flash with the wrapper (as installed from the repos) works great for 99% of people.

As far as having 6GB of memory, you cannot use more than 3.3GB (or something like that) of RAM on a 32 bit system unless you install a special kernel with PAE, which is basically a work-around for people who need more RAM than that, but for whatever reason are unwilling or unable to run 64bit. 

The only area where 64 bit has any performance disadvantage to 32bit, is that it requires more memory.  That makes it a little iffy to put it on a system with 2GB or less, but with 6GB, you won't know the difference, and you'll be able to take FULL advantage of all that ram without having to install a non-standard kernel.



Short version:  For you, go with Ubuntu linux 10.04, 64 bit.

---

### Post by dookiebowser on 2010-06-11
> **an4rew said:**
> I must say the linux community have done some great work, Ubuntu looks very slick!

Should a new user to Ubuntu install the latest distro or the older releases more stable and would i be missing out on anything worthwhile?

I have 6GB ram, is x64 Linux much better than it used to be?

Thanks.


I was thinking about switching to x64 when Adobe started tinkering with 64bit versions of flash for Linux, but they failed and quit apparently. 

[http://www.theregister.co.uk/2010/06/11/64_bit_flash_for_linux_dead/](http://www.theregister.co.uk/2010/06/11/64_bit_flash_for_linux_dead/)

However, you can support more than 4GB of ram without running 64bit pretty easily:

[http://packages.ubuntu.com/karmic/linux-image-2.6.31-14-generic-pae](http://packages.ubuntu.com/karmic/linux-image-2.6.31-14-generic-pae)

---

### Post by eriktheblu on 2010-06-11
Only issues I've run into with 64 bit are Flash (fixed by manual install of the alpha) and a SNES emulator.

---

### Post by an4rew on 2010-06-11
Thanks guys, looking forward to installing 10.04 x64 on my rig :)

---

### Post by KdotJ on 2010-06-11
> **an4rew said:**
> Thanks guys, looking forward to installing 10.04 x64 on my rig :)

I'm sure you're going to love it, 10.04 really is a true masterpiece in my opinion.

---

### Post by sandyd on 2010-06-11
> **dookiebowser said:**
> I was thinking about switching to x64 when Adobe started tinkering with 64bit versions of flash for Linux, but they failed and quit apparently. 

[http://www.theregister.co.uk/2010/06/11/64_bit_flash_for_linux_dead/](http://www.theregister.co.uk/2010/06/11/64_bit_flash_for_linux_dead/)

However, you can support more than 4GB of ram without running 64bit pretty easily:

[http://packages.ubuntu.com/karmic/linux-image-2.6.31-14-generic-pae](http://packages.ubuntu.com/karmic/linux-image-2.6.31-14-generic-pae)
check my signature (adobe tools).
Im one step ahead of em'
The plugin still exists, but it just doesnt' have a download link on the page

---

