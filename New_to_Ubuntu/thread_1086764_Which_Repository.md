---
title: "Which Repository"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Dazed_75 on 2009-03-04
given the name of a specific program or package, how can one find out which of the repositories listed in Software Sources contains that package.

also, is there any way to know if more than one repository has that package?

lastly, is there a pecking order for the case the same package (not necessarily the same version) is in more than one of the repositories in use?

---

### Post by SamNSane on 2009-03-04
> **Dazed_75 said:**
> given the name of a specific program or package, how can one find out which of the repositories listed in Software Sources contains that package.

also, is there any way to know if more than one repository has that package?

lastly, is there a pecking order for the case the same package (not necessarily the same version) is in more than one of the repositories in use?

You can find the data on contents of repositories at [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

When you use Synaptic or Update Manager (or apt-get/apttitude) to update the lists of packages available  or to search for a specific package, the package manager compares the list of what's available from all of the repositories. It should display and / or offer the latest version of a given package among all of the versions available in all of your enabled repositories. You can also use a setting in Synaptic to suppress the display of any given update so that it won't be offered.

I hope that:

a) I actually understand this process as well as I think I do.

b) I explained it in a manner that was understandable.

;)

---

