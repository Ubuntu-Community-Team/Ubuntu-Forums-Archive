---
title: "Not seeing all of my memory??"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by CaptainMark on 2009-09-10
I have two 2gb corsair stick running dual channel but the results from  free -m are below```
mark@mark-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3276        883       2393          0         65        424
-/+ buffers/cache:        393       2883
Swap:         9593          0       9593
mark@mark-desktop:~$ 

```Why can I only see 3.27 gb of memory. This hasnt come up before so what do i do? Noob language please.

---

### Post by QIII on 2009-09-10
If you have integrated graphics, you'll "lose" some to the "memory hole" if your chipset is reserving it.

You may be able to use your BIOS settings to change the limit if that is possible.  You can also try memory remapping in the BIOS.

As an aside, what graphics chipset do you have?

---

### Post by achase79 on 2009-09-10
32-bit OS can only see up to 3.27 GB unless you are using the server kernel.  The 64-bit version will allow you to see all of your ram.

---

### Post by QIII on 2009-09-10
32 bit can use more memory if PAE is enabled.

---

### Post by NoaHall on 2009-09-10
PAE sucks. You might just as well upgrade to 64 bit. It's a lot faster, and it's the future.

---

### Post by scragar on 2009-09-10
> **NoaHall said:**
> PAE sucks. You might just as well upgrade to 64 bit. It's a lot faster, and it's the future.

But support right now is, unfortunately, lacking.

---

### Post by QIII on 2009-09-10
> **NoaHall said:**
> PAE sucks. You might just as well upgrade to 64 bit. It's a lot faster, and it's the future.

No doubt...

But it's of little value if your hardware architecture does not support it.

For the OP:  Can you post your machine's specs?

---

### Post by NoaHall on 2009-09-10
> **scragar said:**
> But support right now is, unfortunately, lacking.

Support isn't lacking! It's just as good support as for 32 bit! And for the apps when there isn't support, you can force. I haven't encountered a app yet I haven't been able to install and run on 64 bit. Flash Alpha works even better than the 32 bit version on the 32 bit OS!

64 bit support on Windows sucks, yes, but on Linux, the OS of choice and customization, who says anything is limiting you but your knowledge?

---

### Post by QIII on 2009-09-10
> **scragar said:**
> But support right now is, unfortunately, lacking.

Which support am I lacking on the two machines I currently run the 64 bit version on?

---

### Post by XCan on 2009-09-10
> **scragar said:**
> But support right now is, unfortunately, lacking.

I haven't found any issues at all from running 64bit on two of my machines vs 32bit on the third machine. Ok, I admit, I had to google how to get flash working properly, but it was an easy fix.

Perhaps you're confusing it with Win XP 64bit? :)

---

### Post by bodhi.zazen on 2009-09-10
> **achase79 said:**
> 32-bit OS can only see up to 3.27 GB unless you are using the server kernel.  The 64-bit version will allow you to see all of your ram.

That is not true and karmic has a pae desktop kernel.

[http://packages.ubuntu.com/karmic/linux-image-2.6.31-10-generic-pae](http://packages.ubuntu.com/karmic/linux-image-2.6.31-10-generic-pae)

> 
 Geared toward 32 bit desktop systems with more then 4GB RAM. 
 You likely do not want to install this package directly. Instead, install the linux-generic-pae meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed.

---

### Post by egalvan on 2009-09-10
> **bodhi.zazen said:**
> That is not true and karmic has a pae desktop kernel.

[http://packages.ubuntu.com/karmic/linux-image-2.6.31-10-generic-pae](http://packages.ubuntu.com/karmic/linux-image-2.6.31-10-generic-pae)

Hey Bodi, does the *default* install of Karmic include the

  linux-image-2.6.31-10-generic-pae 

kernel?

Or is this an option? From what I can understand, it's an option to install via Syntaptic.

Up until Jaunty the 32bit Desktop default kernel was non-PAE, 
while the 32bit Server default kernel had PAE enabled.

---

### Post by bodhi.zazen on 2009-09-10
> **egalvan said:**
> Hey Bodi, does the *default* install of Karmic include the

  linux-image-2.6.31-10-generic-pae 

kernel?

Or is this an option? From what I can understand, it's an option to install via Syntaptic.

Up until Jaunty the 32bit Desktop default kernel was non-PAE, 
while the 32bit Server default kernel had PAE enabled.

No, the pae kernel is not the default, you may install it as an option.

Prior to 9.10 you needed to compile it yourself, use the server kernel (sub optimal), and so this makes it easier.

---

### Post by CaptainMark on 2009-09-11
My spec asus mn 378 mobo, 2 x 2gb corsair memory, nvidia geforce 9400gt graphics. amd x2 64,  i am fully 64 compatible and would make the switch if i didnt keep hearing people say the support is not as good, dont get into that again though. would i have to do a clean reinstall to go 64bit??

---

### Post by NoaHall on 2009-09-11
A clean reinstall, yes, but there's no problem with support now - Flash is great , better than the 32bit version.

---

### Post by SunnyRabbiera on 2009-09-11
> **bodhi.zazen said:**
> No, the pae kernel is not the default, you may install it as an option.

Prior to 9.10 you needed to compile it yourself, use the server kernel (sub optimal), and so this makes it easier.

Wow, that does seem easy.
Now I need more RAM to justify it!
:D

---

### Post by egalvan on 2009-09-14
> **bodhi.zazen said:**
> No, the pae kernel is not the default, you may install it as an option.

**Prior to 9.10 you needed to compile it yourself, use the server kernel (sub optimal), **and so this makes it easier.

Are you saying that the SERVER kernel is sub-optimal?
or that having to compile it yourself was sub-optimal?

And on this subject, I just installed the SERVER version of Ubuntu,
then loaded the DE of my choice...

```
sudo apt-get install ubuntu-desktop
```

```
sudo apt-get install kubuntu-dekstop
```

or for a leaner install

```
sudo apt-get install kubuntu-core
```

```
sudo apt-get install xfce-core
```

I did this on several machines that I wanted to use 32-bit versions on, but wanted access to more than 4G RAM.

Ran a treat, they did :guitar:

---

### Post by The Cog on 2009-09-14
> **egalvan said:**
> Are you saying that the SERVER kernel is sub-optimal?
or that having to compile it yourself was sub-optimal?

I think he means that the server kernel is optimised for server throughput rather than for desktop responsiveness, so it's not optimal for a desktop user.

---

### Post by 3rdalbum on 2009-09-14
> **CaptainMark said:**
> My spec asus mn 378 mobo, 2 x 2gb corsair memory, nvidia geforce 9400gt graphics. amd x2 64,  i am fully 64 compatible and would make the switch if i didnt keep hearing people say the support is not as good, dont get into that again though. would i have to do a clean reinstall to go 64bit??

Yes, you need a clean reinstall.

The people who say that there's little 64-bit support either:

1. Used 64-bit Ubuntu a long time ago
2. Are regurgitating what they've heard regarding 64-bit Windows, which is not true for Linux and might not even be true for Windows.

The only "gotcha" is that you need an alpha version of Flash from the Adobe Labs website. Don't let this worry you, it's very stable and actually better than using the 32-bit version on 64-bit.

---

### Post by scragar on 2009-09-14
> **3rdalbum said:**
> Yes, you need a clean reinstall.

The people who say that there's little 64-bit support either:

1. Used 64-bit Ubuntu a long time ago
2. Are regurgitating what they've heard regarding 64-bit Windows, which is not true for Linux and might not even be true for Windows.

The only "gotcha" is that you need an alpha version of Flash from the Adobe Labs website. Don't let this worry you, it's very stable and actually better than using the 32-bit version on 64-bit.

Actually I'm thinking of the hassle it is to get things like skype or wine working if they don't get provided in repo's for whatever reason(Or heaven forbid there's a package you want that's not in the repo's that only comes in 32 bit binary).

Don't get me wrong, I've never had any trouble with such things, but that's because I've always used packages prepared by someone else. I tried this hassle once to get Opera working(before they offered a 64 bit release), I gave up after about 20 minutes.

---

### Post by 3rdalbum on 2009-09-14
> **scragar said:**
> Actually I'm thinking of the hassle it is to get things like skype or wine working if they don't get provided in repo's for whatever reason(Or heaven forbid there's a package you want that's not in the repo's that only comes in 32 bit binary).

Skype now comes with ia32-libs as a dependency and works beautifully.

Wine is in the repos.

Anything that's not provided in a package needs to be compiled anyway, whether you're on 32-bit or 64-bit.

You can install the contents of 32-bit Debian packages on a 64-bit machine - just drag and drop the contents of the "data.tar.gz" into your filesystem.

---

### Post by scragar on 2009-09-14
> **3rdalbum said:**
> Skype now comes with ia32-libs as a dependency and works beautifully.

Wine is in the repos.

Anything that's not provided in a package needs to be compiled anyway, whether you're on 32-bit or 64-bit.

You can install the contents of 32-bit Debian packages on a 64-bit machine - just drag and drop the contents of the "data.tar.gz" into your filesystem.
There are some things that do not come with source, closed source applications. The only way to use those aps is to work around and install lib32 versions.
Yes the average person will not run into such a problem but they do exist, to deny the existence of them is foolish and arrogant.

---

### Post by XCan on 2009-09-14
Haven't found any packages that do not work with 64-bit yet (besides flash through wrapper), or packages missing for the 64-bit platform but existing for the 32-bit platform.

---

### Post by bodhi.zazen on 2009-09-14
> **The Cog said:**
> I think he means that the server kernel is optimised for server throughput rather than for desktop responsiveness, so it's not optimal for a desktop user.


Both.

It is sub optimal to use the server kernel on a desktop (works fine on servers).

It is also sub optimal to "require" people to build a custom kernel to use PAE. first it is difficult fo rnew users to do so and second a custom kernel will not automatically upgrade when a new kernel becomes available. In addition one may need to delve deep into the kernel if they are wanting to use LUKS, some wireless drivers, nvidia, etc.

Fedora has had a PAE kernel for some time and IMO it is nice that Ubuntu has finally offered one as well.

---

### Post by 3rdalbum on 2009-09-14
> **scragar said:**
> There are some things that do not come with source, closed source applications. The only way to use those aps is to work around and install lib32 versions.
Yes the average person will not run into such a problem but they do exist, to deny the existence of them is foolish and arrogant.

If, in the unlikely event that you need to (I haven't needed to for six months or longer), there is Getlibs, that makes it easy to get the 32-bit libraries.

I've had proprietary games running on 64-bit Linux even though they are 32-bit binaries, with no use of Getlibs.

And actually I'm looking at a package called ia32-libs-tools which promises to convert i386-labelled Debs to amd64 Debs, so it could be easy to use 32-bit Debian packages on 64-bit without force-architecture.

---

