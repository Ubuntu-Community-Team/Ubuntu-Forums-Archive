---
title: "I need help figuring out how to recover my system"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by scared0o0rabbit on 2010-03-03
So I had a fresh install of Ubuntu on my new (to me, it's old) laptop the other day.  This morning I started doing the updates, after downloading them all, part way through installing all of the updates it said it needed to restart for the updates to take effect.  I hit restart later, because there were other updates that it was still trying to install.

The computer restarted anyway =/.  Now when I try and load up Ubuntu it just sits at:

*Starting init crypto disks...

It's not totally hung as using the reisub trick will restart the computer.

I figure I probably need to re-install Ubuntu to fix this, right?  Is there some process I can use that will keep my existing software settings and all that, or would it be better to just do a clean wipe and start it over again?  Or is there some other way of fixing this?

Any help would be greatly appreciated.

---

### Post by DubyBreaks on 2010-03-03
I haven't experienced this but was browsing through and saw your post.  It looks like there may be some help in [THIS THREAD]("http://ubuntuforums.org/showthread.php?p=8001869#post8001869")?  It may be what you are experiencing.

---

### Post by Elfy on 2010-03-03
me neither, but this might help - bear in mind if you have grub2 that you will need shift and not esc to see a hidden grub menu

[http://ubuntuforums.org/showpost.php?p=8457528&postcount=7](http://ubuntuforums.org/showpost.php?p=8457528&postcount=7)

---

### Post by scared0o0rabbit on 2010-03-03
So I ended up booting from a live disc and then doing a chroot into my install based on the instructions found here: [http://ubuntuforums.org/showthread.php?t=1267093&page=2](http://ubuntuforums.org/showthread.php?t=1267093&page=2)

Then I did a sudo apt-get update and it told me something was wrong with dpkg and that I needed to run dpkg --configure -a, so I did that, and it took several minutes, after which I rebooted.  The computer hung, so I cycled the power, at which time it booted into Ubuntu just fine, but the login screen was a little funky looking, like the skin didn't really load correctly or something.  I was able to log in just fine though.

I'm going to reboot again and see if it's normal the next time.

Edit:

Loading the update manager before my reboot indicates there are still 113 updates left to download and install.

---

### Post by scared0o0rabbit on 2010-03-03
After updating and rebooting everything seems to be back to normal, looks like this one is solved.

---

