---
title: "How do I remove a package and all associated dependencies"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by guest_user on 2009-12-28
that the package uses but NOT USED by any other installed packages, in other words orphan packages

---

### Post by AgentZ86 on 2009-12-28
Hi

How did you install the package ?

I use Ubuntu, but hopefully some of this info will still help.

The best thing to use if it's not located in the (ubuntu 9.10 Applications/Ubuntu Software Center) or on earlier versions would be Applications/install remove

But if the package is not listed there to uninstall then you have other options.

I use synaptic manager located at: (System/Administration/Synaptic

Then you can search for the installed package your looking for and it will recommend and dependent packages that may need to uninstall as well

Once in synaptic you can go to (file/history) this will show you what was going on and when and why ?

You can make your decisions based on the package history.

There are probably better console methods but I still like the clicking methods because I'm don't understand the command structure as much yet.


And don't forget to right click on a packages in synaptic to see recommendations for add or removal suggestions.

Most of the time you don't need to worry about that but sometimes there may be something of interest that you may want for those recommended suggestions.

I hope this helps

---

### Post by kansasnoob on 2009-12-28
> **guest_user said:**
> that the package uses but NOT USED by any other installed packages, in other words orphan packages

Running "apt-get -f install" will sometimes prompt to remove unused dependencies using "apt-get autoremove".

More package specific info might be helpful.

---

