---
title: "How to get updated app?"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by mesmith on 2009-08-10
I'm currently using xubuntu 8.10.  Tried an upgrade to 9.04, but too many problems and don't have the time to deal with them now.  I will at some point.  My question is:  I use Abiword a lot.  The version in 8.10 has a broken help system.  I would like to use the latest version of Abiword, or at least the version shipped with 9.04, but there doesn't seem to be a clear path to do so.  Forum help has suggested I ask for a backport.  I did that, but no response.  I also filed bug reports when the broken help first appeared.  No fix in 8.10 but fixed in 9.04.  Why is it so difficult to upgrade an app?  One Forum suggestion was download and compile latest version "it might work."  Whoa!  I'm not interested in a broken app.  Is there some help that you all can give?  Updating an app between versions should be possible - no?

---

### Post by snowpine on 2009-08-10
The way Ubuntu updates work is you never get a major new version of an application through regular updates, just minor security updates. Major updates are lumped together every six months, for example by upgrading to 9.04.

If you just want a new version of one application, go to that app's website and follow their instructions: [http://abisource.com/wiki/Install_on_Ubuntu](http://abisource.com/wiki/Install_on_Ubuntu)

Note however you'll be using a version that is not specifically tested by Canonical for your Ubuntu release, so make sure you trust the application's developer...

---

### Post by Hospadar on 2009-08-10
You might also want to try the "backports" repository.  It contains versions of packages for later versions of ubuntu that won't be added for compatability reasons (package maintainers only put major software updates in new versions of ubuntu so anyone with a production system that works can always update without fear of breaking their environment).

I believe (I'm using KDE so I can't say for sure) if you go to System->Administration->Software Sources you can just check the backports repository and away you go.  It might be located a little different in Xubuntu, but it's in there somewhere.

If that doesn't work, best thing I would think would be to un-install the version you got from the repositories, and then install the version directly from the developers (with the link above)

---

