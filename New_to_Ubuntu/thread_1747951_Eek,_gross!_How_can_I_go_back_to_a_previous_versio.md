---
title: "Eek, gross! How can I go back to a previous version?"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by Baldrick_NZ on 2011-05-03
Hi all, 

having previously downloaded Songbird, I noticed there was an update so clicked on it, only to find that my 'feather' wasn't supported in the updated version. Now I'm stuck with an ugly purple default feather which doesn't look good on my desktop.

So, I'm wondering how I can get rid of this version (without un-installing it first) and roll-back to my previous version? Synaptic doesn't seem to offer a 'rollback' option.

This would probably also answer the question regarding software roll-backs in general. 

Any help would be much appreciated.

Cheers,
baldrick

---

### Post by Baldrick_NZ on 2011-05-04
bump...

---

### Post by wolfen69 on 2011-05-04
What version are you running?

---

### Post by Lateralis on 2011-05-04
Software rollbacks are not possible as far as I know.  The only way to get the older version is to manually install it - either side-by-side with the current version or over the top.

---

### Post by Baldrick_NZ on 2011-05-04
Thanks for the reply.

OS: lucid 10.04.2. 

Songbird: 1.9.3 from the getdeb repo.

---

### Post by wolfen69 on 2011-05-04
> **Lateralis said:**
> Software rollbacks are not possible as far as I know.  The only way to get the older version is to manually install it - either side-by-side with the current version or over the top.
It's actually easy to do if you are using a PPA for the app. You would just uninstall the ppa and install the previous version.

---

### Post by Baldrick_NZ on 2011-05-04
> **wolfen69 said:**
> It's actually easy to do if you are using a PPA for the app. You would just uninstall the ppa and install the previous version.

Ok, so how do you do that? I've been to the getdeb website and they only list this latest version.

---

### Post by beew on 2011-05-04
> **Baldrick_NZ said:**
> Ok, so how do you do that? I've been to the getdeb website and they only list this latest version.

In Synaptic there is an option to roll back (if there is an earlier version in your repositories) Open Synaptic, go to songbird, right click and go to properties and find what versions are available. If you can find an earlier version then you highlight songbird, go to package > force version and pick the version you want and click apply and it will be downgraded to that version, you should then highlight it again and go to package > lock version so that it won't be upgraded.

Now what if you don't have an earlier version in your repo? There are  a few things you can do. 

1) Find a ppa that has an earlier version and add it to the sources list and then downgrade with force version as above.

2) Find a .deb file or a tar ball for an earlier version, uninstall your current version and then install the .deb or tar ball.

3) This may work sometimes but it may be risky. Add the appropriate source from an earlier release of Ubuntu(you can google it) That way you will have an earlier version in your repos. Then downgrade the package using force version in Synaptic as described above, _then remove the source_. You shouldn't do this if your package involves a lot of dependencies. I have mixed repos from different releases this way without breaking things but I always make sure the applications I want are more or less self contained in that they have no or very few external dependencies so that messing with them would not affect other softwares.

---

