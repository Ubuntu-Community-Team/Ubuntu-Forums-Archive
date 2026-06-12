---
title: "a newbies experience"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by Blockdor on 2010-11-04
Hi
been thinking of using linux for a while, got a new netbook (HP mini 311) and thought ok lets go.

My friend suggested wubi.

So i download wubi and run it, decide to use the netbook version (since its a netbook).

So yeah, doesn't work. searched these forums and it turns out wubi is version 10.4.1 while the netbook iso is 10.4 so they're incompatible. 
the great thing about this is that wubi downloads via torrent, then again, then again so used up 2.1gb of download bandwidth on a file it should know isn't going to work (the clue was in the file name).

ok so nevermind, by this point i've set it off maybe 3/4 times (10gb of wasted download) and i think ok i'll just try the desktop version.

Works fine first time, so i'm now thinking "great! ubuntu is actually easy to install" everything's going well, ubuntu finds all my drivers, even wireless works out of the box. "Most impressive"

However, first thing ubuntu does is open the software updates utility. 

Fine i think, these are critical security updates, better get them.

So i let it do it's thing and then restart. 
blam 
"udevadm trigger not permitted while udev is unconfigured"
ALERT! /dev/sha1 does not exist.

And now i'm in a shell which doesn't seem to do much other than list directories.

OK. now i've no idea what to do, i check this forum, try a patch for wubildr, edit some settings, no avail.
though i do hear while i'm looking for answers that wubi is only really for trying out ubuntu and making it easier to install for a test run.

Well i have to say it needs to be a bit easier.

recommendations for wubi from my end are... 
if it doesn't suppoprt an iso don't download it, error before downloading 2gb of iso.

If the default software updates break whatever magic wubi is using to dual boot without a partition either disable the update that does this or put a big banner on the wubi page saying "this is for trials only, don't update!" the former is better as users are idiots.

As it stands i'm ok with creating a partition so that's what i'll do now..
but yeah if we're trying to get over the stigma of linux which i see as
"breaks and leaves you at a command prompt with no idea what to do"
wubi's obviously doing ubuntu no favours.

Maybe it's just my netbook but please check this cause ubuntu is great (what l've used so far by reinstalling and not updating anything) and it'd be a shame to put people off.

my 2c

cheers

Alex

---

### Post by sandyd on 2010-11-04
> **Blockdor said:**
> Hi
been thinking of using linux for a while, got a new netbook (HP mini 311) and thought ok lets go.

My friend suggested wubi.

So i download wubi and run it, decide to use the netbook version (since its a netbook).

So yeah, doesn't work. searched these forums and it turns out wubi is version 10.4.1 while the netbook iso is 10.4 so they're incompatible. 
the great thing about this is that wubi downloads via torrent, then again, then again so used up 2.1gb of download bandwidth on a file it should know isn't going to work (the clue was in the file name).

ok so nevermind, by this point i've set it off maybe 3/4 times (10gb of wasted download) and i think ok i'll just try the desktop version.

Works fine first time, so i'm now thinking "great! ubuntu is actually easy to install" everything's going well, ubuntu finds all my drivers, even wireless works out of the box. "Most impressive"

However, first thing ubuntu does is open the software updates utility. 

Fine i think, these are critical security updates, better get them.

So i let it do it's thing and then restart. 
blam 
"udevadm trigger not permitted while udev is unconfigured"
ALERT! /dev/sha1 does not exist.

And now i'm in a shell which doesn't seem to do much other than list directories.

OK. now i've no idea what to do, i check this forum, try a patch for wubildr, edit some settings, no avail.
though i do hear while i'm looking for answers that wubi is only really for trying out ubuntu and making it easier to install for a test run.

Well i have to say it needs to be a bit easier.

recommendations for wubi from my end are... 
if it doesn't suppoprt an iso don't download it, error before downloading 2gb of iso.

If the default software updates break whatever magic wubi is using to dual boot without a partition either disable the update that does this or put a big banner on the wubi page saying "this is for trials only, don't update!" the former is better as users are idiots.

As it stands i'm ok with creating a partition so that's what i'll do now..
but yeah if we're trying to get over the stigma of linux which i see as
"breaks and leaves you at a command prompt with no idea what to do"
wubi's obviously doing ubuntu no favours.

Maybe it's just my netbook but please check this cause ubuntu is great (what l've used so far by reinstalling and not updating anything) and it'd be a shame to put people off.

my 2c

cheers

Alex

[https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654](https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654)

ill give the bug a little poke for ya.

---

### Post by anewguy on 2010-11-04
While this is a bug, it's still wubi.  Things like this is why I recommend staying away from wubi and either just using the LiveCD for a while or install to a USB flash drive (if your system allows boot from USB - mine doesn't - it's too old).  That way you can test drive ubuntu and if you like it then do a regular install.  In reality, this is all wubi is meant to be - a way to ubuntu without changing your system - then do a regular install.

Just my 2-cents worth (if it's even worth that).

Best of luck, and glad to see another person ready to at least try ubuntu.  If you've followed the forum, yes there can be "problems" (usually just a missing driver or boot line parameter) but these are normally solved quite easily.

Dave ;)

---

### Post by Carl Hamlin on 2010-11-04
> **anewguy said:**
> Things like this is why I recommend staying away from wubi and either just using the LiveCD for a while or install to a USB flash drive (if your system allows boot from USB - mine doesn't - it's too old).

If you *do* decide to install to USB, keep in mind that flash sports a finite number of write/erase cycles, and running a complete operating system on it is going to use those up in a hurry.

Make sure you save your data to a more robust medium to avoid tears.

---

### Post by anewguy on 2010-11-04
> **Carl Hamlin said:**
> If you *do* decide to install to USB, keep in mind that flash sports a finite number of write/erase cycles, and running a complete operating system on it is going to use those up in a hurry.

Make sure you save your data to a more robust medium to avoid tears.

100% correct - I didn't actually end up typing what my mind was thinking and didn't know it until you posted back.  I didn't mean to actually install to USB and run it forever - just to take a look and then do a full install (non-wubi).  Thanks for pointing this out.  As a side note, some of the old flash drives used to have relatively low usage rate, whereas the newer ones have gotten a lot better.  What people forget is the huge number of IO's that happen just within the OS, let alone any program you run.

thanks again!
Dave ;)

---

### Post by mastablasta on 2010-11-05
as i understand...
 
...if it's only live USB install it should be ok because data is then mostly just read form the disk and transfered into the RAM.
 
where problems might occur is full/propper USB install or maybe with persistant install. but even then i don't actually know how it really works (and how much it damages the USB) as it is just a live USB with a persistent file that's supposed to save any changes to live system.
 
heh wubi... seems people have a lot of issues with it. if oyu ask me they should fix these issues and then put it up as an option. or at least as the OP said put some big warning about it instead of pretending that everything is working great in wubi.

---

