---
title: "Everything Has Disappeared!"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by chrishawkes84 on 2007-05-08
Hey!
I recently installed Fiesty on my laptop and everything was working lovely across my wireless connection. I had file sharing working, icons of my access point and computers appearing in Places -> Network, but now they have all disappeared and file sharing has died as well.
It is all connecting to the network fine over the wireless connection and I have internet acesss, its just file sharing has gone, and them icons disappearing as well doesnt seem to be a good sign!
Any help in remedying this would be really appreciated! :)

---

### Post by sudo_nym on 2007-05-08
Hmm...  Just a guess, but have you had any updates lately?  I don't mean upgrading to Feisty or anything, but regular software updates and stuff.

There have been a *lot* of posts about people having wireless trouble after a kernel update.  A few examples;

[http://ubuntuforums.org/showthread.php?t=428835](http://ubuntuforums.org/showthread.php?t=428835)
[http://ubuntuforums.org/showthread.php?t=405051](http://ubuntuforums.org/showthread.php?t=405051)
[http://ubuntuforums.org/showthread.php?t=413594](http://ubuntuforums.org/showthread.php?t=413594)

I'm guessing the kernel on the install CD it a little older than what's in the repositories, so it might have done an update when you weren't looking.  Have you tried booting from an older kernel?  [try hitting ESC as soon as Grub starts to load.  Should give you a list of boot options].

I had a similar, but totally unrelated experience when Opera suddenly stopped working, for no apparent reason, and for a couple days I couldn't figure out why.  Turns out it had to do with updating libx11 [as noted here, if anyone's curious; [http://ubuntuforums.org/showthread.php?t=401508](http://ubuntuforums.org/showthread.php?t=401508)].

That was about the time I disabled auto-updates.  Nothing against upgrading software, usually beneficial, but if you explicitly agree to something in the update manager, you're more likely to remember what system components have been changed recently when something stops working.

Have a look at Synaptic's `History' list [in File > History, just above the `Quit' menu item], and look for recent updates to networking software -- like whatever happened the day before it broke.



Good luck,

Patrick.

---

