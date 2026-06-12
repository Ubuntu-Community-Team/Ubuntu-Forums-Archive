---
title: "No Wireless Adapter in 10.10 - need NDIS Wrapper but no internet connection"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by carusoswi on 2011-01-15
OK, perhaps I should already know how to do this, but, I installed Ubuntu to my dual boot machine (replaced 9.10 Studio with fresh install).  Everything went as I expected, but, the new installation does not recognize my wireless adapter (a Lynksys Wireless G).  I have the driver for the wireless, just need to install it into Ubuntu.

I know I could download NDIS Wrapper, but I cannot do that without a connection to the Internet.

I can access the 'net via my XP OS, but, how would I get the NDIS wrapper and how would I install it into Ubuntu once obtained?

If I disassemble my set up and relocate it to a location in my house where a wired connection is available, I could solve this problem in ten seconds, but I'm thinking I should be able fix this without a wired connection if I knew the proper steps.

Help, anyone?

Thanks.

Caruso

---

### Post by TeoBigusGeekus on 2011-01-15
Go to [this]("http://sourceforge.net/projects/ndiswrapper/files/") page with xp, download the version you want (latest stable recommended).
Then boot up in ubuntu, take the archive on an ubuntu partition, extract it and install it following the instructions.

---

### Post by carusoswi on 2011-01-15
This problem was solved with information gleaned from the following thread:

[http://ubuntuforums.org/showthread.php?t=1632352](http://ubuntuforums.org/showthread.php?t=1632352)

I wish I new how to mark this thread solved, but I don't see where you do that - perhaps someone can explain.

Anyway, thanks to anewguy for the compete explanation.

I have always loved Ubuntu, and little problems like this don't bother me much, but, I imagine they could be very frustrating to someone with less layman level experience in several OS's such as myself.

Given a choice, I could happily forgo my work in favor of stumbling around exploring OS's and how they work.  But many are unlike me, and for them, details such as this could prove to be deal killers if they are trying out Ubuntu.

I am no lazier (and probably not much more inquisitive) than the next guy or gal, so, I'm wondering why something that has to have become so basic as getting your wifi adapter to work when it is your only avenue to the internet is not made more obvious during the installation process.

I guess there are reasons for not making NDIS installation part of the LiveCD installation (although I cannot imagine what that reason might be), but I'm thinking the option to install it (or return to the LiveCD to install it as I did (after being wised up by anewguy)) should be made much more prominent during any new installation procedure.

All complaining aside, it is still wonderful that I could sign on here and find a solution with relatively little effort.

Thanks again, anewguy.

Caruso:p

---

