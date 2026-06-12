---
title: "Software Center doesn't show Install Buttons"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by Corinthians on 2010-02-26
Allrighty.  I've been trying to get this to work for a while now and since my attempts have failed I have to come to request assistance!

I'm trying to install the ubuntu-restricted-extras on a live boot of Ubuntu 9.10 using a casper-rw file. But when I go to install it from Ubuntu Software Center there is no install button. I have read numerous times on this forum that all you need to do is update your machine and it should work.  I have updated my machine via Update Manager, checked for upgrades with Synaptic, ran sudo apt-get update.  And each time it comes back and says that I'm completely up to date and there's nothing to install.

But when I got to Software center there still is no button to install and when I search synaptic it doesn't show up.

I would love to know what I'm doing wrong so that I can stop having this problem.

Thanks!
Corinthians.

---

### Post by Dougie187 on 2010-02-26
If I'm not mistaken it's because you are on a live cd.

I don't know if you can install it on a live cd because it's a larger package and all. But if you want to try, just make sure the repositories are installed in synaptic.

go to Settings->Repositories

On the Ubuntu Software tab, Check the box next to multiverse 

Then you can close it, and reload your sources. Then it may or may not show up.

Edit: To further explain. I think that on a live cd the only "repository" you can install software from (by default) is the cd. And ubuntu-restricted-extras is not included on a live cd. So you can't install it without editing your sources. Also keep in mind, any changes you make to a live cd session will be undone when you reboot. Meaning if you want ubuntu-restricted-extras the next time you boot into it, you will have to go through all of these steps again.

---

### Post by Corinthians on 2010-03-01
Thank You very much!  Ah the joys of overlooking something that I probably should have seen.

It worked perfectly!

Once more... THANKS!
Corinthians

---

