---
title: "Updates"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by Rayve on 2010-05-22
Good morning,

When I look at the list of Updates available from Update Manager, do I need to install everything under the "Security Update" section?  Such as the MIT Kereberos libraries, or maybe like SAMBA since I don't use it... do I still need to install the updates there?  Or can I ignore them?

If I can ignore them, is there a way to have Update Manager automatically ignore items if I don't have the main program installed?

Thanks!

---

### Post by 3rdalbum on 2010-05-22
> **Rayve said:**
> Good morning,

When I look at the list of Updates available from Update Manager, do I need to install everything under the "Security Update" section?  Such as the MIT Kereberos libraries, or maybe like SAMBA since I don't use it... do I still need to install the updates there?  Or can I ignore them?

You could ignore them, but **the best policy is to install all updates**. If you pick and choose updates you could break your system. For instance: You want a shiny new version of Plymouth, but that "mountall" update sounds useless? Whoops, you've probably just prevented your system from being able to boot, because Plymouth and Mountall are intertwined. Usually an update that depends on other updates will not be installable separately (it will pull in the other update as well), but sometimes human error by the package maintainer will cause this relationship to not be enforced.

It won't take up many minutes of your life to install these updates, and it certainly won't take up much disk space at all. Just update and save yourself trouble down the track. This goes especially for security updates, as they are more important to your safety than mere bugfix updates; and security updates should NEVER break anything.

> If I can ignore them, is there a way to have Update Manager automatically ignore items if I don't have the main program installed?

You only receive update notifications for things you already have installed. **Samba (the client) is preinstalled on Ubuntu**, which is why you get a notification. If there's an update available for a package you don't have, then you won't be notified and your system won't download it; but if you try to install that package at some point, you'll automatically get the latest version.

---

### Post by AlexDudko on 2010-05-22
Surely you can ignore them if only they depend on other packages you can't get rid of.

---

### Post by HermanAB on 2010-05-22
Depends on how you use your machine.

If it works properly, then an update cannot make it better.  It can leave it the same, or worse.  If you are willing to take the risk of ending up with a machine that is worse after the update than before, then go ahead and do the updates...

I never do updates on a machines that work properly.  I rather re-install the whole thing once a year from scratch, apply updates till it works properly, then I leave it alone till the next year.

I do keep an eye on security updates, but it must be something very, very serious before I would do an update on a working machine.

---

### Post by Rayve on 2010-05-22
Thanks for your responses, everyone!  :)  Disk space isn't an issue really, I was just concerned that installing/updating things I didn't use might introduce more security risks into the mix.

I'll go ahead and install all updates to be safe.

Thanks again!

---

